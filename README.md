# Ansible Configuration Repository

This repository contains Ansible playbooks for RHEL system administration.

## Available Roles

- `system_update`: Handles system updates and patches
- `security_hardening`: Implements basic security configurations
- `user_management`: Manages system users and access
- `postgres_setup`: Installs and configures PostgreSQL server

## Usage

1. Update inventory with your RHEL hosts
2. Configure admin_users in site.yml
3. Add SSH public keys in roles/user_management/files/
4. Run the playbook:
   ```bash
   ansible-playbook site.yml
   ```

### PostgreSQL Setup
To install PostgreSQL on database servers:
