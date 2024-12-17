# Ansible Configuration Repository

This repository contains Ansible playbooks for RHEL system administration.

## Available Roles

- `system_update`: Handles system updates and patches
- `security_hardening`: Implements basic security configurations
- `user_management`: Manages system users and access
- `postgres_setup`: Installs and configures PostgreSQL server
- `rhel9-cis`: Implements CIS Security Benchmarks for RHEL 9

## Usage

1. Update inventory with your RHEL hosts
2. Configure admin_users in site.yml
3. Add SSH public keys in roles/user_management/files/
4. Run the playbook:
   ```bash
   ansible-playbook site.yml
   ```

### CIS Compliance Implementation

To apply CIS security standards to RHEL 9 systems:

1. Review and adjust CIS settings in `roles/rhel9-cis/defaults/main.yml`
2. Run the CIS compliance playbook:
   ```bash
   ansible-playbook site-cis.yml
   ```

You can also run specific CIS sections using tags:
```bash
ansible-playbook site-cis.yml --tags "section1,section2"
```

Available CIS sections:
- section1: Initial Setup
- section2: Services
- section3: Network Configuration
- section4: Logging and Auditing
- section5: Access and Authentication
- section6: System Maintenance

### PostgreSQL Setup
To install PostgreSQL on database servers:
