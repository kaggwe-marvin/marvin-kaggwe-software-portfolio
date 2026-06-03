# Deployment Guide (VPS + GitHub Actions + Docker)

This document is a practical checklist for deploying typical projects in this portfolio to a **VPS** using **Docker** and **GitHub Actions**.

> Goal: **accomplish repeatable deployments** as measured by **one-command server setup + automated deploys on push** by **standardizing Docker images, secrets, and a minimal release process.**

---

## 0) Assumptions
- You have a VPS (Ubuntu 22.04+ recommended)
- You have a domain (optional but recommended)
- You have SSH access to the server
- Your app can run in Docker

---

## 1) Server bootstrap (one-time)
### Create a deploy user
```bash
sudo adduser deploy
sudo usermod -aG sudo deploy
```

### SSH hardening
- Add your SSH public key to `/home/deploy/.ssh/authorized_keys`
- Disable password auth (recommended)

Edit:
```bash
sudo nano /etc/ssh/sshd_config
```
Suggested:
```text
PasswordAuthentication no
PermitRootLogin no
```
Restart:
```bash
sudo systemctl restart ssh
```

### Install Docker
```bash
curl -fsSL https://get.docker.com | sudo sh
sudo usermod -aG docker deploy
newgrp docker
```

### Install utilities
```bash
sudo apt-get update
sudo apt-get install -y git ufw
```

### Firewall (UFW)
```bash
sudo ufw allow OpenSSH
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable
sudo ufw status
```

---

## 2) App layout on the server
A simple, consistent layout helps automation:

```text
/opt/apps/
  myapp/
    docker-compose.yml
    .env
    data/
```

Create:
```bash
sudo mkdir -p /opt/apps/myapp
sudo chown -R deploy:deploy /opt/apps/myapp
```

---

## 3) Docker Compose template (typical web app)
Create `docker-compose.yml` in `/opt/apps/myapp`:

```yaml
services:
  app:
    image: ghcr.io/<owner>/<repo>:latest
    restart: unless-stopped
    env_file:
      - .env
    ports:
      - "3000:3000"
    depends_on: []

  # Example DB (optional):
  # db:
  #   image: postgres:16
  #   restart: unless-stopped
  #   environment:
  #     POSTGRES_DB: app
  #     POSTGRES_USER: app
  #     POSTGRES_PASSWORD: change_me
  #   volumes:
  #     - ./data/postgres:/var/lib/postgresql/data

networks:
  default:
    name: myapp_net
```

Then run:
```bash
cd /opt/apps/myapp
docker compose up -d
docker compose logs -f --tail=200
```

---

## 4) Reverse proxy + TLS (recommended)
Two common patterns:

### Option A: Caddy (simple)
- Automatically manages HTTPS certificates.
- Great default for small VPS setups.

Example Caddyfile:
```text
mydomain.com {
  reverse_proxy localhost:3000
}
```

### Option B: Nginx + Certbot
- More manual but widely used.

---

## 5) GitHub Actions CI/CD checklist
### Recommended pipeline stages
- **Lint / tests** (fast feedback)
- **Build Docker image**
- **Push image to registry** (GHCR recommended)
- **Deploy**: SSH into VPS → pull image → restart compose

### Required secrets (repo settings)
Set these in GitHub repo → Settings → Secrets and variables → Actions:
- `VPS_HOST` (IP or hostname)
- `VPS_USER` (e.g., `deploy`)
- `VPS_SSH_KEY` (private key for deploy user)
- `APP_ENV` (optional: env contents)

### Deployment strategy (simple)
On each push to `main`:
1) Build image
2) Push `:latest` (or `:${{ github.sha }}`)
3) SSH to server
4) `docker compose pull && docker compose up -d`

---

## 6) Secrets / environment variables
### Rules
- Never commit real secrets
- Use `.env` on server for runtime config
- Keep sample values in `.env.example` in the repo

Example `.env`:
```bash
NODE_ENV=production
PORT=3000
DATABASE_URL=postgres://...
```

---

## 7) Operational checklist
### After deploy
- Confirm health:
  - `docker ps`
  - `docker compose logs -f --tail=200`
  - hit `/health` endpoint if you have one
- Verify disk usage:
  - `df -h`
- Monitor memory:
  - `free -h`

### Backups (recommended)
- For SQLite: back up the DB file when the app is stopped or using a safe copy method.
- For Postgres/MySQL: scheduled dumps or volume backups.

---

## 8) Common pitfalls
- **Ports**: ensure firewall and reverse proxy are aligned.
- **Permissions**: docker group membership for deploy user.
- **DB migrations**: consider running migrations as part of deploy.
- **Logs**: ensure logs are persisted or shipped.

---

## 9) Optional improvements
- Add a `/health` endpoint
- Add log rotation
- Add monitoring (Uptime Kuma, Prometheus, etc.)
- Use image tags by commit SHA for safe rollbacks

---

## Notes for this portfolio
Some projects here use:
- **Bun + Hono + SQLite** (simple single-VPS deployment)
- **Node.js + relational DB** (compose with Postgres/MySQL)
- **Workflow automation + dashboard** (keep services small, use stable logging)
