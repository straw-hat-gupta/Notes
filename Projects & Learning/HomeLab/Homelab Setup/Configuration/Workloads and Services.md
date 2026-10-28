# Workloads and Services

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]] · [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Configuration|Open questions]]

Checked 2026-10-27, 21:37–21:42 MDT. Sources: Proxmox resources/configuration, LXC inspection, QEMU guest-agent queries, Docker metadata, systemd service state, and HTTP readiness checks.

## Guests

| ID | Name | Type / host | Purpose | OS | CPU allocation | RAM | Swap | Start at boot |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 301 | llm-gpu | VM / pve-d1 | Career Ops; remote workspace with GPU passthrough | Ubuntu 24.04.4 LTS | 1 socket × 6 vCPUs | 24 GiB | Managed inside guest | Yes |
| 100 | app-runner | Unprivileged LXC / pve-d2 | AI dashboard | Ubuntu 24.04.4 LTS | 1 core | 1 GiB | 512 MiB | Yes; order 10, up 30s, down 60s |
| 101 | cf-tunnel | Unprivileged LXC / pve-d2 | Cloudflare tunnel | Ubuntu 24.04 LTS | 2 cores | 512 MiB | 512 MiB | Not explicitly enabled in configuration |
| 201 | monitoring | Unprivileged LXC / pve-6420 | Metrics, dashboards, and alerting | Ubuntu 24.04.4 LTS | 2 cores | 4 GiB | 512 MiB | Yes |

All four guests were running. No guests were listed on pve-storage or pve-7450 at collection time.

LXC 100 and 201 have `nesting=1,keyctl=1`; LXC 101 has `nesting=1`. VM 301's machine, CPU type, guest agent, and passthrough settings are in [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Cluster Configuration#GPU passthrough|Cluster Configuration]]. Disk volumes are in [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Guest disk assignments|Storage Configuration]], and IP/MAC/bridge settings are in [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Guest connections|Network Configuration]].

## Services

| Service | Location | Endpoint / listener | Runtime / configuration |
| --- | --- | --- | --- |
| AI dashboard | LXC 100 | `http://10.44.0.220:4200/` | Docker container `ai-dashboard`, image `ai-dashboard-ai-dashboard`; Compose `/opt/ai-dashboard/docker-compose.yml` |
| Cloudflare tunnel | LXC 101 | Outbound tunnel; [[Projects & Learning/HomeLab/Project Hosting/Open Questions\|public routes to confirm]] | `cloudflared.service`, active |
| Grafana | LXC 201 | `http://10.44.0.80:3000` | Docker `grafana`, image `grafana/grafana-oss:latest` |
| Prometheus | LXC 201 | `http://10.44.0.80:9090` | Docker `prometheus`, image `prom/prometheus:latest` |
| Alertmanager | LXC 201 | `http://10.44.0.80:9093` | Docker `alertmanager`, image `prom/alertmanager:latest` |
| Proxmox exporter | LXC 201 | `http://10.44.0.80:9221` | Docker `pve-exporter`, image `prompve/prometheus-pve-exporter:latest` |
| Node exporter | All five Proxmox hosts | `http://NODE_IP:9100/metrics` | `prometheus-node-exporter.service`, active |
| Tailscale | VM 301; also installed on pve-d2 per ANSWERS | `tailscale0`; [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Access\|network record]] | VM 301: `tailscaled.service` active; D2 runtime not collected |
| CAO server | VM 301 | `127.0.0.1:9889` | Process `cao-server` listening; application purpose/configuration still [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Configuration\|to reconcile with Career Ops]] |
| Ollama | VM 301 | `127.0.0.1:11434` | Existing `ollama.service`, active; no model inventory or serving test |
| Career Ops | VM 301, confirmed in [[Projects & Learning/HomeLab/ANSWERS\|ANSWERS]] | Accessed through llm-gpu; process/configuration details still [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Configuration\|to document]] | [[Projects & Learning/Projects/Career Ops/Career Ops\|Career Ops project notes]] |

Monitoring Compose file: `/opt/monitoring/docker-compose.yml`. Grafana depends on Prometheus; Prometheus scrapes five host exporters, five Proxmox targets, and itself. All 11 targets were up during the check. Service health and current faults are in [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]].

## Planned service reconfiguration

Career Ops needs reconfiguration. I want it packaged in Docker or an equivalent portable setup, remotely accessible, and automatically recovered on another node if its host fails. I want the same hosting approach available to other services, tools, and projects. Confirmed in [[Projects & Learning/HomeLab/ANSWERS|ANSWERS]], 2026-10-27.

The deployment/failover requirements are maintained in [[Projects & Learning/HomeLab/Project Hosting/Project Hosting#Service portability and recovery|Project Hosting]]. The current llm-gpu placement and GPU passthrough are unchanged.

## Service data and configuration locations

Paths below are inside the indicated LXC. There are no configured extra host bind mounts in the collected LXC configuration, so these paths reside on the container root disks.

| Guest / service | Persistent data | Configuration |
| --- | --- | --- |
| 100 / AI dashboard | `/opt/ai-dashboard/data` → container `/data` | `/opt/ai-dashboard/docker-compose.yml` |
| 201 / Prometheus | `/opt/monitoring/data/prometheus` → `/prometheus` | `/opt/monitoring/prometheus/prometheus.yml`; `/opt/monitoring/prometheus/rules` |
| 201 / Grafana | `/opt/monitoring/data/grafana` → `/var/lib/grafana` | `/opt/monitoring/grafana/provisioning` |
| 201 / Alertmanager | `/opt/monitoring/data/alertmanager` → `/alertmanager` | `/opt/monitoring/alertmanager/alertmanager.yml` |
| 201 / Proxmox exporter | No separate data mount listed | `/opt/monitoring/pve-exporter/pve.yml` (credential-bearing contents excluded) |

Backup coverage is recorded in [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Backups, replication, and shares|Storage Configuration]].

[[Projects & Learning/HomeLab/Homelab Setup/Evidence/2026-10-27.json|Evidence snapshot]]
