Monitoring Stack with CI/CD Pipeline
Overview
A production-style monitoring infrastructure built on an Ubuntu Server VM, featuring automated deployment via a self-hosted GitHub Actions CI/CD pipeline.
Why Self-Hosted Runner
Instead of using GitHub cloud runners with inbound SSH, a self-hosted runner was installed directly on server-vm. The runner initiates an outbound connection to GitHub — no ports need to be opened, and no credentials are exposed in the workflow file. This mirrors how internal CI/CD is handled in real MSP and enterprise environments.
Stack Components

Prometheus — metrics collection and storage
Grafana — dashboards and visualization (port 3000)
cAdvisor — Docker container metrics (port 8080)
Node Exporter — host system metrics (port 9100)
GitHub Actions Runner — self-hosted, runs as a systemd service

CI/CD Pipeline
Workflow triggers on every push to main:

Runner detects the push event
Pulls latest code from GitHub
Runs docker compose up -d --build to redeploy the stack

Infrastructure Details

Host: Ubuntu Server 26.04 LTS on VirtualBox
IP: 10.10.10.10 (internal network: labnet)
Runner version: 2.335.1

Skills Demonstrated

CI/CD pipeline design and implementation
Self-hosted runner security architecture
Docker Compose service orchestration
systemd service management
Linux server administration
Infrastructure monitoring with Prometheus and Grafana
