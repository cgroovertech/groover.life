# 🚀 Christian Groover - DevOps Portfolio

**`@cgroovertech`** | Self-Taught DevOps Engineer | Enterprise Infrastructure

[![Portfolio](https://img.shields.io/badge/Portfolio-Live-brightgreen)](https://cgroovertech.github.io/groover.life)
[![GitHub](https://img.shields.io/badge/GitHub-cgroovertech-blue)](https://github.com/cgroovertech)
[![Infrastructure](https://img.shields.io/badge/Focus-Kubernetes%20|%20Automation-orange)](https://github.com/cgroovertech)

---

## 🎯 **Showcase Highlights**

• **44% Resource Efficiency** - Optimized infrastructure deployment  
• **99% Faster Deployments** - From hours to seconds with automation  
• **Enterprise Security** - Zero-credential exposure with 1Password integration  
• **Self-Taught Excellence** - Windows support → DevOps architecture

## 🏗️ **Deployment Architecture**

```mermaid
graph TB
    subgraph "Control Plane"
        Mac["MacBook Pro<br/>💻 Development"]
        Git["GitHub<br/>💾 Source Control"]
    end
    
    subgraph "Infrastructure Layer"
        Proxmox["Proxmox VE<br/>🏗️ Hypervisor"]
        Net["VyOS Router<br/>🌐 Network"]
    end
    
    subgraph "Kubernetes Cluster"
        K3s["K3s Master<br/>⚙️ Orchestrator"]
        Traefik["Traefik<br/>🌍 Ingress"]
        GitLab["GitLab CE<br/>🤖 CI/CD"]
    end
    
    subgraph "Services Layer"
        Auth["Authelia<br/>🔐 SSO/MFA"]
        DNS["Bind9<br/>🎯 DNS"]
        Vault["1Password<br/>🗝️ Secrets"]
        DB["PostgreSQL<br/>🗄 Database"]
    end
    
    Mac --> Git
    Git --> GitLab
    Mac --> Proxmox
    Proxmox --> K3s
    Net --> Traefik
    K3s --> Traefik
    K3s --> GitLab
    K3s --> Auth
    K3s --> DNS
    K3s --> DB
    Vault --> GitLab
    
    style Mac fill:#e1f5fe
    style Git fill:#f3e5f5
    style K3s fill:#e8f5e8
    style Traefik fill:#fff3e0
```

### 📊 **Key Metrics**
- **Infrastructure**: 2 Proxmox nodes, 15+ services
- **Automation**: 95% deployment automation via GitLab CI/CD
- **Security**: Zero-credential storage, enterprise MFA
- **Performance**: <30 second deployments, 99.9% uptime

## 📚 **Featured Projects**

### 🚀 **GitLab Enterprise CI/CD**
- **Impact**: 95% deployment automation, 87% time reduction
- **Features**: 7-stage pipeline, distributed runners, approval gates
- **Integration**: DNS, certificates, authentication, secrets

### 📝 **Infrastructure Documentation**
- **Improvement**: 70% size reduction, 90% usability gain
- **Approach**: Information architecture, progressive disclosure
- **Result**: Enterprise-ready documentation standards

### 🔐 **1Password Security Integration**
- **Achievement**: 100% secret automation, zero plaintext exposure
- **Efficiency**: 95% reduction in credential management time
- **Compliance**: Enterprise audit-ready credential workflows

## 🔧 **Tech Stack**

**Container Orchestration**  
`Kubernetes` • `K3s` • `Docker` • `Helm`

**Infrastructure**  
`Proxmox` • `VyOS` • `Terraform` • `Ansible`

**CI/CD & Security**  
`GitLab CE` • `1Password` • `Authelia` • `Traefik`

**Databases & Monitoring**  
`PostgreSQL` • `Bind9` • `Prometheus` • `Grafana`

## 🔗 **Links & Contact**

- **Portfolio**: https://cgroovertech.github.io/groover.life  
- **GitHub**: https://github.com/cgroovertech  
- **Email**: contact@groover.life

---

## 📄 **Featured Reading**

**Showcase Articles**
- [The Self-Taught Path](showcase/self-taught-path.md)
- [Lessons Learned](showcase/lessons-learned.md)
- [Architecture Decisions](showcase/architecture-decisions.md)

**Project Case Studies**
- [GitLab CI/CD Platform](projects/gitlab-cicd.md)
- [Documentation Restructure](projects/documentation-restructure.md)
- [1Password Integration](projects/1password-integration.md)

---

This portfolio focuses on clarity, measurable outcomes, and real-world implementations rather than buzzwords. If you’d like the deeper technical breakdowns, see the case studies and articles above.
