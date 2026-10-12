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
