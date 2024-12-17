# 🚀 Ansible Configuration Repository

Your one-stop shop for RHEL system automation! This repository makes system administration a breeze.

## 🎯 Quick Start

### First Time Setup
1. 📦 Get Ansible running:
   ```bash
   sudo dnf install ansible   # Just one command and you're ready!
   ```

2. 🔑 Set up your SSH keys (because typing passwords is so 1990s):
   ```bash
   ssh-keygen -t ed25519    # Hit enter a few times
   ssh-copy-id user@target-host
   ```

## 🛠️ Super Powers (Available Roles)

| Role | What it Does |
|------|-------------|
| 🔄 `system_update` | Keeps your systems fresh and up-to-date |
| 🛡️ `security_hardening` | Makes your servers fortress-like |
| 👥 `user_management` | Handles the "who can do what" stuff |
| 🐘 `postgres_setup` | PostgreSQL magic |
| 🎯 `rhel9-cis` | CIS compliance (for the serious stuff) |
| 🌐 `httpd` | Apache web server setup |
| 🗄️ `mariadb` | MariaDB database setup |
| 🐘 `php` | PHP and modules |
| 📦 `redis` | Redis cache server |
| 🚦 `nginx` | Nginx web server |
| 📊 `monitoring` | System monitoring tools |

## Service Installation

Install common services using tags:
```bash
# Install web server and PHP
ansible-playbook site-services.yml --tags "web"

# Install just MariaDB
ansible-playbook site-services.yml --tags "database"

# Install everything
ansible-playbook site-services.yml
```

Enable specific services in your inventory:
```yaml
all:
  hosts:
    webserver:
      enable_httpd: true
      enable_php: true
    dbserver:
      enable_mariadb: true
```

## 🎡 OpenShift Installation

Deploy a production-ready OpenShift cluster:

```bash
# Verify prerequisites only
ansible-playbook playbooks/openshift-install.yml --tags prereq

# Full installation
ansible-playbook playbooks/openshift-install.yml

# Install without monitoring
ansible-playbook playbooks/openshift-install.yml --skip-tags monitoring
```

### Prerequisites
- OpenShift Pull Secret from Red Hat
- Valid cloud provider credentials
- DNS configuration
- Required tools:
  - openshift-install
  - oc
  - kubectl
  - cloud provider CLI

## 🎭 MicroK8s Installation

Deploy a production-ready MicroK8s cluster:

```bash
# Install full cluster
ansible-playbook -i inventory/microk8s.yml playbooks/microk8s-install.yml

# Install without monitoring
ansible-playbook -i inventory/microk8s.yml playbooks/microk8s-install.yml --skip-tags monitoring

# Add new node to cluster
ansible-playbook -i inventory/microk8s.yml playbooks/microk8s-install.yml --limit new_node.example.com
```

### MicroK8s Features
- High Availability Setup
- Built-in Monitoring
- Automatic RBAC
- Load Balancing (MetalLB)
- Certificate Management
- Container Registry
- Automated Backups

## 💡 Pro Tips

1. Always start with `--check` when trying something new
2. Use tags to run specific parts of a playbook
3. Keep your inventory updated and organized
4. Take backups before major changes

Need more help? Check out our [Wiki](https://github.com/your-repo/wiki) or create an issue!
