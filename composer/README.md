# RHEL 9 Cloud-Init Blueprint

This directory contains blueprints for building custom RHEL 9 images with cloud-init support.

## Prerequisites

- RHEL 9 system with composer-cli installed
- Valid Red Hat subscription
- Root or sudo access

## Installation

```bash
# Install composer-cli if not already installed
sudo dnf install -y composer-cli

# Start and enable osbuild-composer service
sudo systemctl enable --now osbuild-composer.socket
```

## Using the Blueprint

1. Push the blueprint to composer:
```bash
composer-cli blueprints push rhel9-cloud-init.toml
```

2. Check if blueprint is listed:
```bash
composer-cli blueprints list
```

3. Build the image:
```bash
composer-cli compose start rhel9-cloud-init qcow2
```

4. Check build status:
```bash
composer-cli compose status
```

5. Download the finished image:
```bash
composer-cli compose image <UUID>
```

## Blueprint Details

The `rhel9-cloud-init.toml` blueprint includes:
- cloud-init for cloud instance initialization
- OpenSSH server for remote access
- Python 3 for automation support
- NetworkManager for network configuration
- Preconfigured services for cloud deployment

## Customization

Modify the `rhel9-cloud-init.toml` file to:
- Add/remove packages
- Change default hostname
- Enable/disable services
- Add custom repositories
- Configure system parameters

## Troubleshooting

- Check logs with: `composer-cli compose logs <UUID>`
- Verify blueprint: `composer-cli blueprints depsolve rhel9-cloud-init`
- Debug services: `systemctl status osbuild-composer`
