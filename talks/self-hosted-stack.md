# The Self Hosted Stack
Having your own cloud, control the data
## Why
- Keep your data
- Privacy
- Terms change, free systems become paid
- Risk in someone else having it
- Subscriptions
## Before you start
- pick your uses cases
## Hardware
- mini PC
- used business PC
    - sold in bulk
- old desktop
## Choosing the platform
- NAS operating systems
- Linux
- Hypervisor
    - Proxmox
- VMs
    - full isolation
## Stack
- Files
    - Google drive alt
    - Nextcloud
        - all in one office suite
        - a little bloated
- Images
    - immmich
- Media
    - Jellyfin
    - Plex having "issues"
- Passwords
    - vaultwarden
- Home automation
    - Home Assistant
        - combines many different smart devices
    - Frigate
        - camera recordings
- Local names and HTTPS
    - nginx proxy manager
    - local top level domain
- other apps
    - adguard home
    - paperless-ngx
        - document management and OCR
    - uptime kuma
    - mealie
## Accessing securely
- netbird, other providers
- private network at home
- private dns
    - work from away from home
- host on vps externally
- can be self hosted
## Backing up
- 3-2-1 backup philosphy
    - 3 copies
    - 2 different meida
    - 1 offsite
        - encrypted copies to 3rd party services
- Proxmox backup server
- S3-compatible storage offsite
## Monitoring
- Grafana
- Prometheus
- InfluxDB
