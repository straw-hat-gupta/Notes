# Homelab Status

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status|Status questions]]

Live baseline: **2026-10-27, 21:37–21:42 MDT**. Later reports below are dated separately; the baseline does not establish health after the updates.

## Reported changes — 2026-10-28

I updated all five nodes. During E7450's web-UI update it disconnected from the cluster without a reboot initiated by me. Its boot/reachability/recovery state is unverified. The incident is recorded in [[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]].

Exact package/running-kernel versions and the cause of the disconnect remain pending.

## D1/storage investigation — 2026-10-28

[[Projects & Learning/HomeLab/Node Issues/D1 and Storage Evidence|D1 and Storage Evidence]] records three corroborated historical D1 e1000e transmit stalls with network isolation, and a separate June D1 pressure/task stall. Storage's August departures were maintenance; its June abrupt log ending and the undated reported fault remain unresolved. The exact D1 component/trigger and a lasting fix are not established.

At approximately **10:42 MDT**, both target nodes were reachable, with working 1 Gb/s full-duplex nic0 links, and present in a quorate component with 4 total votes, 5 expected votes, and quorum threshold 3. The scoped current versions are in [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Cluster Configuration#Scoped version check — 2026-10-28|Cluster Configuration]]. Other nodes' incident records were not reassessed.

Current target `rx_errors`, `tx_errors`, and `tx_timeout_count` counters were zero; they do not reconstruct pre-reboot faults. All six target disks passed SMART overall status. D1's Toshiba boot SSD has one historical ATA error-log entry without an incident calendar correlation; it does not establish a disk cause. Command provenance and values are in [[Projects & Learning/HomeLab/Node Issues/Evidence/2026-10-28/Baseline.json|Baseline]].

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
| E7450 disconnected during an update | Reported 2026-10-28; no manually initiated reboot. Automatic reboot, link loss, and cluster-only loss are still to distinguish. | [[Projects & Learning/HomeLab/Node Issues/Open Questions\|Node Issues questions]] |
| VM 301 NVIDIA driver unavailable | `nvidia-smi` exited 9: unable to communicate with the NVIDIA driver. The GTX 1070 is visible at guest PCI `06:10.0`, with no driver-in-use entry for its display function. | [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status\|T1]] |
| `openipmi.service` failed on all five hosts | `systemctl --failed` and unit state show `failed`, result `exit-code`. | [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status\|T2]] |
| Historical D1/storage dropouts | Three D1 transmit-stall episodes corroborated; separate June D1 task stall and storage fault remain unresolved. No fix validated. | [[Projects & Learning/HomeLab/Node Issues/D1 and Storage Evidence\|D1 and Storage Evidence]] |

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

IPMI (Intelligent Platform Management Interface) is a hardware-management interface for monitoring sensors and related platform functions. Whether these systems need OpenIPMI for the desired readings remains to be established. CPU temperatures and SMART readings were already collected while the unit was failed; diagnosis should identify available hardware and any missing metric coverage. A failed unit alone does not identify the dropout cause. [Linux IPMI documentation](https://docs.kernel.org/driver-api/ipmi.html).

## Protection and exposure

No backups have been established as of 2026-10-27. [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Backups, replication, and shares|Backup records]] also show no configured Proxmox backup jobs or listed local backup archives. Configured storage has no disk redundancy. [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Firewall|Proxmox firewall]] reports disabled/running on all hosts; other access boundaries are in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|Open Questions]].

Sources: `pvecm status`, `systemctl`, `uptime`, `/proc/meminfo`, `sensors`, `smartctl`, guest runtime inspection, HTTP readiness requests, and Prometheus target status. [[Projects & Learning/HomeLab/Homelab Setup/Evidence/2026-10-27.json|Evidence snapshot]].
