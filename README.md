# Mini VAIO Homelab

A lightweight self-hosted homelab running on an old VAIO laptop with only 2 GB of RAM.

This project was created as a practical environment to study and experiment with Linux, Docker, networking, monitoring, security, backups and DevOps concepts using limited hardware resources.

Instead of relying only on theoretical knowledge, the goal of this homelab is to build, operate and document real services.

---

## Hardware

| Component | Specification |
|---|---|
| Device | VAIO Laptop |
| RAM | 2 GB |
| Storage | 500 GB HDD |
| Architecture | x86_64 |
| Operating System | Debian Linux |

Because of the limited hardware resources, one of the main goals of this project is to keep the infrastructure lightweight and efficient.

---

## Current Infrastructure

The server currently runs Docker containers and uses Tailscale for remote access.

### Services

- **Docker**
  - Container runtime used to host the services.

- **Tailscale**
  - Provides secure remote access to the homelab without exposing services directly to the internet.

- **Caddy**
  - Reverse proxy responsible for HTTPS and TLS certificates.

- **Vaultwarden**
  - Self-hosted password manager compatible with Bitwarden clients.

- **Uptime Kuma**
  - Monitoring platform used to check service availability and uptime.

---

## Architecture (image made with text editor nano)

```text
Remote Device
     |
     |
  Tailscale
     |
     v
+-----------------------+
|      Mini VAIO        |
|      Debian Linux     |
|                       |
|       Docker          |
|          |            |
|   +------+-------+    |
|   |      |       |    |
| Caddy  Vault-   Uptime|
|        warden    Kuma |
|                       |
+-----------------------+
```
Caddy acts as a reverse proxy for services that require HTTPS.  
Tailscale allows remote access to the server and its services without requiring public port forwarding.  

---

# Docker Structure
The current environment is organized using Docker Compose.

```text
docker/
├── vaultwarden/
│   ├── docker-compose.yml
│   └── Caddyfile
│
└── uptime-kuma/
    └── docker-compose.yml
```
The directory structure may change as the homelab grows.

---

# Monitoring    
Uptime Kuma is currently responsible for monitoring service availability.      
Planned monitoring includes:       
- Vaultwarden availability
- HTTPS endpoints
- TLS certificate validity
- Docker containers
- Disk usage
- RAM usage
- CPU load
- HDD SMART health
- Server temperature
Lightweight Bash scripts may be used to send system metrics to Uptime Kuma Push Monitors.      
---

# Backup      
Backup implementation is currently planned.   
Possible technologies being evaluated:   
- Restic
- Automated backup scripts
- Scheduled backups using cron
- Encrypted backups
- Off-site backup storage

The backup strategy will prioritize low resource usage because the server only has 2 GB of RAM.    

---   

# Security     
Current security practices include:  
- UFW as firewall, that only allow port 22 to ssh    
- Remote access through Tailscale  
- HTTPS using Caddy
- No unnecessary public ports exposed
- Containerized services
- Encrypted communication
- Limited hardware attack surface
Additional hardening will be implemented as the project evolves.
---

# Goals     
This homelab is mainly used to develop practical knowledge in:
- Linux administration
- Docker
- Docker Compose
- Networking
- Reverse proxies
- HTTPS / TLS
- VPN / overlay networks
- Monitoring
- Backup strategies
- Bash scripting
- Infrastructure troubleshooting
- DevOps practices
---

# Why this project?    
The goal of this project is not to build a large production infrastructure.
The challenge is actually the opposite:
How much useful infrastructure can be built using an old laptop with only 2 GB of RAM?

This constraint encourages the use of lightweight tools, resource optimization and a better understanding of how each service consumes system resources.
The project also serves as a practical portfolio documenting my progress with Linux, infrastructure and DevOps.   

---
# Status
Work in progress    
