# Homelab Status

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status|Status questions]]

Observed **2026-10-27, 21:37–21:42 MDT**. This is a point-in-time snapshot.

## Hosts and cluster

All five hosts were reachable as root over SSH. The cluster was quorate with 5 of 5 votes and a quorum threshold of 3. Host management services, SSH, and node exporters were active on all nodes.

| Node | Reachability / membership | Last boot (MDT) | Available RAM (GiB) | Load average (1 / 5 / 15 min) | CPU package |
| --- | --- | --- | --- | --- | --- |
| pve-d1 | Reachable; cluster member | 2026-10-27 14:50:03 | 4.79 | 0.07, 0.15, 0.16 | 41 °C |
| pve-d2 | Reachable; cluster member | 2026-09-24 10:27:49 | 13.04 | 0.01, 0.02, 0.00 | 41 °C |
| pve-storage | Reachable; cluster member | 2026-10-27 15:40:47 | 21.40 | 0.19, 0.24, 0.21 | 39 °C |
| pve-6420 | Reachable; cluster member | 2026-08-23 13:38:58 | 3.31 | 0.41, 0.14, 0.11 | 55 °C |
| pve-7450 | Reachable; cluster member | 2026-08-23 13:28:38 | 13.56 | 0.02, 0.04, 0.05 | 67 °C |

## Guests and applications

All four configured guests were running: VM 301 on pve-d1, LXC 100/101 on pve-d2, and LXC 201 on pve-6420.

| Check | Result |
| --- | --- |
| Grafana `/api/health` | HTTP 200 |
| Prometheus `/-/ready` | HTTP 200 |
| Alertmanager `/-/ready` | HTTP 200 |
| Proxmox exporter `/` | HTTP 200 |
| AI dashboard `/` | HTTP 200 |
| Prometheus active targets | 11/11 up: five host exporters, five Proxmox targets, Prometheus itself |
| Cloudflare tunnel service | Active in LXC 101; public routing not tested |
| VM 301 guest agent | Responds to network, OS, and command queries |

Endpoints and service configuration: [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]].

## Active faults

| Fault | Evidence | Follow-up |
| --- | --- | --- |
| VM 301 NVIDIA driver unavailable | `nvidia-smi` exited 9: unable to communicate with the NVIDIA driver. The GTX 1070 is visible at guest PCI `06:10.0`, with no driver-in-use entry for its display function. | [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status\|T1]] |
| `openipmi.service` failed on all five hosts | `systemctl --failed` and unit state show `failed`, result `exit-code`. | [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status\|T2]] |
| Earlier D1/storage dropouts remain unresolved | Both are reachable now; this does not confirm the cause or a lasting recovery. | [[Projects & Learning/HomeLab/Node Issues/Open Questions\|Node Issues questions]] |

## Disk and temperature observations

All nine disks reported SMART overall status passed. No extended disk self-tests were run.

| Disk | Selected SMART observation |
| --- | --- |
| D1 Samsung 850 EVO (`/dev/sda`) | Attribute 5: normalized 99, threshold 10, raw 1; wear-leveling normalized 96 |
| E7450 Samsung PM851 (`/dev/sda`) | Attribute 5: normalized 91, threshold 10, raw 189; wear-leveling normalized 81, threshold 5 |
| Storage Seagate HDD (`/dev/sda`) | 49,555 power-on hours; reallocated, pending, and offline-uncorrectable raw values 0 |
| Storage WD HDD (`/dev/sdb`) | 9,755 power-on hours; reallocated, pending, and offline-uncorrectable raw values 0 |
| E6420 WD HDD (`/dev/sda`) | 12,345 power-on hours; reallocated, pending, and offline-uncorrectable raw values 0 |

SMART raw fields are vendor-specific; trend and interpretation are tracked in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status|T4]]. Disk temperatures where reported ranged from 22–38 °C. CPU package temperatures are in the host table above; no package critical-alarm flag was set.

`sensors` could not read one fan field on D2/storage and one wireless temperature field on E7450. Those readings are unavailable, rather than evidence of a failed fan or overheating.

IPMI (Intelligent Platform Management Interface) is a hardware-management interface for monitoring sensors and related platform functions. Whether these systems need OpenIPMI remains to be established; a failed unit alone does not identify the dropout cause. [Linux IPMI documentation](https://docs.kernel.org/driver-api/ipmi.html).

## Protection and exposure

[[Projects & Learning/HomeLab/ANSWERS|ANSWERS]] confirms that no backups have been established as of 2026-10-27. [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Backups, replication, and shares|Backup records]] also show no configured Proxmox backup jobs or listed local backup archives. Configured storage has no disk redundancy. [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Firewall|Proxmox firewall]] reports disabled/running on all hosts; other access boundaries are in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|Open Questions]].

Sources: `pvecm status`, `systemctl`, `uptime`, `/proc/meminfo`, `sensors`, `smartctl`, guest runtime inspection, HTTP readiness requests, and Prometheus target status. [[Projects & Learning/HomeLab/Homelab Setup/Evidence/2026-10-27.json|Evidence snapshot]].
