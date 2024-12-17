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

## Inventory Setup

Create or modify the inventory file (`inventory.yml`):
```yaml
all:
  children:
    rhel9_servers:
      hosts:
        db01.example.com:
        web01.example.com:
      vars:
        ansible_user: admin
    postgres_servers:
      hosts:
        db01.example.com:
```

## 📝 Getting Started (The Fun Part!)

### Test if Everything's Working
```bash
ansible all -i inventory.yml -m ping   # Like saying "hello" to all your servers
```

### Common Commands (Your Daily Toolkit)

🔧 **Basic Operations:**
```bash
# Update all the things!
ansible-playbook -i inventory.yml system-update.yml

# Make one server extra secure
ansible-playbook -i inventory.yml security.yml --limit web01.example.com
```

### 🎯 CIS Compliance Made Easy

Want to make your RHEL 9 systems super secure? We've got you covered!

```bash
# The "make everything secure" button:
ansible-playbook site-cis.yml

# Just the network stuff:
ansible-playbook site-cis.yml --tags "section3"

# Preview mode (look before you leap):
ansible-playbook site-cis.yml --check --diff
```

Available Security Sections:
- 📁 section1: Initial Setup
- 🔌 section2: Services
- 🌐 section3: Network Configuration
- 📝 section4: Logging and Auditing
- 🔐 section5: Access and Authentication
- 🛠️ section6: System Maintenance

### 🔍 Quick Health Checks

Check on your servers' health:
```bash
# Who's awake?
ansible all -i inventory.yml -m command -a "uptime"

# Got space?
ansible all -i inventory.yml -m command -a "df -h"
```

### 🆘 Troubleshooting

When things go sideways:
```bash
# Extra verbose mode (for the curious minds)
ansible-playbook site.yml -vvv

# Dry run (for the cautious souls)
ansible-playbook site.yml --check
```

## 📁 Project Map
```
.
├── 📄 inventory.yml
├── 📄 site.yml
├── 📄 site-cis.yml
├── 📂 roles/
│   ├── 🔄 system_update/
│   ├── 🛡️ security_hardening/
│   ├── 👥 user_management/
│   ├── 🐘 postgres_setup/
│   └── 🎯 rhel9-cis/
└── 📂 playbooks/
    ├── user.yml
    └── maintenance.yml
```

## 💡 Pro Tips

1. Always start with `--check` when trying something new
2. Use tags to run specific parts of a playbook
3. Keep your inventory updated and organized
4. Take backups before major changes

Need more help? Check out our [Wiki](https://github.com/your-repo/wiki) or create an issue!
