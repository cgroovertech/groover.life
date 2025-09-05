# PAM systemd SSH Authentication Delays in LXC Containers

## Problem Description

SSH connections to LXC containers experience 25-30 second delays during authentication, making automation and interactive access unusably slow.

## Root Cause

The `pam_systemd.so` module attempts to register user sessions with `systemd-logind`, but `systemd-logind` fails to start in LXC containers due to namespace restrictions.

### Technical Details

```bash
# Error in systemd-logind service
systemd-logind.service: Failed to set up mount namespacing: /run/systemd/unit-root/proc: Permission denied
systemd-logind.service: Failed at step NAMESPACE spawning /lib/systemd/systemd-logind: Permission denied
```

**Authentication Flow**:
1. SSH connection established
2. PAM authentication chain starts
3. `pam_systemd.so` tries to contact `systemd-logind`
4. `systemd-logind` is down/failing
5. **25-second timeout waiting for systemd response**
6. PAM continues with authentication
7. SSH session finally established

## Impact

- **SSH Performance**: 25-30 second connection delays
- **Automation**: Ansible/Terraform operations become unusably slow
- **Interactive Access**: Poor user experience for container management
- **Monitoring**: False timeout alerts in monitoring systems

## Solution

### Option 1: Disable pam_systemd.so (Recommended for Containers)

Disable systemd session management in containers where it's not needed:

```bash
# Backup original configuration
cp /etc/pam.d/common-session /etc/pam.d/common-session.bak

# Disable pam_systemd.so
sed -i 's/session\s*optional\s*pam_systemd.so/#&/' /etc/pam.d/common-session

# Verify change
grep pam_systemd /etc/pam.d/common-session
```

**Result**: SSH connections become instant (sub-1 second)

### Option 2: Configure pam_systemd.so with Timeout

If systemd session tracking is required:

```bash
# Add timeout to prevent long delays
sed -i 's/session\s*optional\s*pam_systemd.so/& timeout=1/' /etc/pam.d/common-session
```

## Security Implications

**Disabling pam_systemd.so**:
- ✅ **No authentication bypass** - Core PAM auth modules remain active
- ✅ **SSH key authentication** - Unaffected, works normally  
- ✅ **User/group permissions** - Unchanged
- ⚠️ **Session tracking** - systemd won't track user sessions
- ⚠️ **Resource limits** - systemd-based limits won't apply

**Container Context**:
- LXC containers don't typically need desktop session management
- Resource limits handled by container runtime (Proxmox)
- Session tracking less critical in containerized services

## Implementation

### Automated Fix for All Containers

```bash
# Apply fix to all running containers
for container in $(pct list | grep running | awk '{print $1}'); do
    echo "Fixing PAM in container $container"
    pct exec $container -- cp /etc/pam.d/common-session /etc/pam.d/common-session.bak
    pct exec $container -- sed -i 's/session\s*optional\s*pam_systemd.so/#&/' /etc/pam.d/common-session
done
```

### Verification

```bash
# Test SSH performance
time ssh user@container-ip 'echo "Connection test"'
# Should be < 2 seconds
```

## Prevention

### Container Template Configuration

Add to container templates/ansible roles:

```yaml
- name: Optimize PAM for containers
  lineinfile:
    path: /etc/pam.d/common-session
    regexp: '^session\s*optional\s*pam_systemd\.so'
    line: '#session	optional	pam_systemd.so'
    backup: yes
```

### Service User Creation Workflow

1. Create service user with proper shell and home directory
2. Configure passwordless sudo
3. Deploy SSH keys
4. **Fix PAM systemd configuration**
5. Test SSH connectivity

## Related Issues

- **systemd-logind namespace errors** in container logs
- **SSH timeout warnings** in monitoring systems  
- **Ansible connection timeouts** during playbook execution
- **Interactive terminal delays** for manual access

## References

- [systemd-logind in containers](https://systemd.io/CONTAINER_INTERFACE/)
- [PAM configuration guide](https://linux.die.net/man/5/pam.conf)  
- [LXC systemd limitations](https://linuxcontainers.org/lxc/manpages/man5/lxc.container.conf.5.html)

---

**Created**: 2025-09-05  
**Author**: Homelab Infrastructure Team  
**Tested**: Proxmox LXC containers (Debian/Ubuntu base)
