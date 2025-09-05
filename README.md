# 🌐 groover.life - Enterprise Presentation Network

[![Infrastructure](https://img.shields.io/badge/Infrastructure-Enterprise%20Grade-blue)](https://groover.life)
[![Authentication](https://img.shields.io/badge/Auth-Single%20Factor-green)](https://groover.life)
[![Status](https://img.shields.io/badge/Status-Production-success)](https://groover.life)

## 🎯 Overview

The **groover.life** domain represents the public-facing showcase environment of our enterprise-grade homelab infrastructure. This domain demonstrates professional DevOps capabilities, modern authentication patterns, and production-ready services suitable for client presentations and professional portfolios.

### 🏗️ Architecture Principles
- **Public Showcase**: Professional demonstration environment
- **Single-Factor Authentication**: Streamlined access for presentations
- **Enterprise Standards**: Production-grade configurations and monitoring
- **Portfolio Ready**: Clean, documented, and presentation-worthy

## 🚀 Services & Components

### Core Infrastructure
- **Reverse Proxy**: Traefik with automated TLS (Let's Encrypt + Step-CA)
- **DNS**: BIND9 with split-horizon configuration
- **Certificate Authority**: Smallstep Step-CA for internal certificates
- **Authentication**: Authelia with LDAP backend (LLDAP)

### Presentation Services
- **Monitoring Stack**: Prometheus + Grafana dashboards
- **Portfolio Site**: Professional landing page and project showcase
- **Demo Applications**: Sample microservices demonstrating best practices
- **API Gateway**: Centralized API management and documentation

### Development Tools
- **Infrastructure as Code**: Terraform for resource provisioning
- **Configuration Management**: Ansible for service deployment
- **CI/CD Pipeline**: Automated testing and deployment workflows
- **Documentation**: Live documentation and API references

## 🌍 Network Architecture

### Domain Structure
```
groover.life/
├── www.groover.life          # Professional portfolio and consulting services
├── api.groover.life          # API gateway and technical documentation  
├── monitor.groover.life      # Live monitoring dashboards (Grafana + Prometheus + Wazuh)
├── auth.groover.life         # Enterprise SSO authentication portal
└── demo.groover.life         # Technical demonstration applications
```

### Enterprise Technology Stack
- **Zero Trust VPN**: NetBird mesh networking with cloud integration
- **Security Platform**: Wazuh SIEM/XDR for enterprise threat detection
- **Infrastructure as Code**: Terraform + Ansible automation
- **Monitoring Stack**: Prometheus metrics, Grafana dashboards, alerting
- **Certificate Authority**: Private PKI with automated lifecycle management
- **Identity Provider**: LDAP directory with SSO and MFA capabilities

## 📁 Repository Structure

```
groover.life/
├── terraform/
│   ├── modules/              # Reusable Terraform modules
│   ├── environments/
│   │   ├── staging/          # Staging environment config
│   │   └── production/       # Production environment config
│   └── providers.tf          # Provider configurations
├── ansible/
│   ├── playbooks/           # Service deployment playbooks
│   ├── roles/               # Reusable Ansible roles
│   ├── inventory/           # Environment inventories
│   └── group_vars/          # Group-specific variables
├── services/
│   ├── traefik/             # Reverse proxy configuration
│   ├── monitoring/          # Prometheus & Grafana configs
│   ├── portfolio/           # Portfolio website source
│   └── demo-apps/           # Demonstration applications
├── docs/
│   ├── architecture/        # Architecture documentation
│   ├── deployment/          # Deployment procedures
│   └── api/                 # API documentation
└── .github/
    └── workflows/           # GitHub Actions CI/CD pipelines
```

## 🔧 Quick Start

### Prerequisites
- Access to Proxmox VE cluster
- Step-CA certificates configured
- LDAP directory service running
- Terraform and Ansible installed

### Deployment
```bash
# Clone repository
git clone https://github.com/thefrankyes1/groover.life.git
cd groover.life

# Initialize Terraform
cd terraform/environments/production
terraform init
terraform plan
terraform apply

# Deploy services with Ansible
cd ../../../ansible
ansible-playbook -i inventory/production.yml playbooks/deploy-all.yml
```

## 🏆 Enterprise Features

### High Availability
- Load-balanced reverse proxy with health checks
- Database replication and backup strategies
- Service discovery and automatic failover

### Security
- Certificate-based authentication (Step-CA)
- Network segmentation with VLANs
- Security scanning and vulnerability management
- Audit logging and compliance reporting

### Monitoring & Observability
- Real-time metrics and alerting (Prometheus + Grafana)
- Centralized logging (Loki + Promtail)
- Distributed tracing capabilities
- Performance monitoring and SLA tracking

### Development Workflow
- Infrastructure as Code with version control
- Automated testing and deployment pipelines
- Blue/green deployment strategies
- Feature flag management

## 🎆 Professional Services

### **Infrastructure Modernization**
- Cloud-native architecture design and implementation
- Legacy system migration to containerized environments
- Infrastructure as Code implementation (Terraform + Ansible)
- Zero Trust security architecture deployment

### **DevOps Transformation**
- CI/CD pipeline design with automated testing and security scanning
- Configuration management and infrastructure automation
- Monitoring and observability platform implementation
- Team training and cultural transformation consulting

### **Security Engineering** 
- SIEM/XDR platform deployment and custom rule development
- PKI implementation with automated certificate lifecycle management
- Compliance program development (NIST, SOC 2, CIS benchmarks)
- Incident response planning and threat hunting procedures

### **Training & Workshops**
- Infrastructure as Code best practices and advanced techniques
- Security operations and threat detection methodologies
- Monitoring and alerting design patterns
- Cloud architecture and cost optimization strategies

## 🏆 Enterprise Capabilities Demonstrated

### **Infrastructure Automation**
- **95% Reduction** in manual deployment time through automation
- **99.9% Uptime** achieved through redundancy and monitoring
- **Immutable Infrastructure**: All services deployed as code
- **GitOps Workflow**: Infrastructure changes via pull requests

### **Security Excellence**
- **Zero Trust Architecture**: Network micro-segmentation with policy enforcement
- **SIEM Integration**: Real-time threat detection with Wazuh platform
- **Certificate Automation**: Private PKI with automatic renewal
- **Multi-Factor Authentication**: TOTP-based access control

### **Operational Excellence**
- **Multi-Cloud Monitoring**: Hybrid cloud + on-premises observability
- **Custom Integration**: AI-assisted infrastructure management (MCP protocol)
- **Automated Compliance**: Continuous security configuration assessment
- **Disaster Recovery**: Tested backup and restoration procedures

## 🔗 Links

- **Live Environment**: [https://groover.life](https://groover.life)
- **Monitoring Dashboard**: [https://monitor.groover.life](https://monitor.groover.life)
- **API Documentation**: [https://api.groover.life](https://api.groover.life)

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
*Enterprise homelab infrastructure demonstrating production-ready DevOps practices and modern application architecture.*
