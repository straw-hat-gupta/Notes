# Homelab Setup — Open Questions

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]]

Updated 2026-10-28. Confirmed answers are in the maintained records. Remaining investigation and design questions are listed here; work is tracked in [[Projects & Learning/HomeLab/Homelab Setup/Tasks|Tasks]].

## Hardware

Both replacement NICs are uninstalled. Their possible use on D1/storage depends on diagnosis; see [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Replacement NICs|Replacement NICs]]. Other display-card VRAM details are deferred unless needed. There are no hardware-identification questions blocking the diagnosis plan.

## Storage

| ID | Question | Relevant record |
| --- | --- | --- |
| S1 | Where are the complete Career Ops installation, configuration, and persistent data, and how should they be backed up/restored? Schedule, retention, and independent/offsite destination still need choosing. | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Immediate backup scope\|Career Ops backup scope]] |
| S4 | What are the tradeoffs of TrueNAS VM versus bare metal on this hardware, including physical-disk access and the spare SSD's boot role? | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Planned TrueNAS setup\|TrueNAS plan]] |
| S5 | Which datasets, shares/protocols, clients, and permissions fit the intended backup, ISO, shared-data, and network-drive use? Explain the choices before selecting them. | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Planned TrueNAS setup\|Shared-storage plan]] |

## Networking

| ID | Question | Relevant record |
| --- | --- | --- |
| N1 | How can equipment labels, router settings, and host configuration establish the exact router/switch models, port map, DHCP scope, and guest reservations? | [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration\|Networking]] |
| N3 | Which default firewall/Tailscale rules currently apply, and which access boundaries suit the intended remote services? | [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Firewall\|Firewall and access]] |
| N4 | What do the existing Cloudflare records/routes do, and what public/private service mapping is needed? | [[Projects & Learning/HomeLab/Project Hosting/Open Questions\|Project Hosting questions]] |

## Configuration

| ID | Question | Relevant record |
| --- | --- | --- |
| C1 | What package versions and running kernels are present after the reported all-node updates? Are reboots or further alignment needed, and what maintenance approach fits the cluster? | [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Cluster Configuration#Host updates and version alignment\|Update status]] |
| C2 | What exact Career Ops files, dependencies, and restore steps are needed for the entire service's move to a dedicated LXC/container? | [[Projects & Learning/HomeLab/Project Hosting/Open Questions\|Service-hosting questions]] |
| C3 | Which foundational configuration and metric-access requirements should be ready before later stack/dashboard selection? | [[Projects & Learning/HomeLab/Monitoring/Open Questions\|Monitoring questions]] |

## Status

| ID | Question | Relevant record |
| --- | --- | --- |
| T1 | Why does nvidia-smi fail in llm-gpu, and what repair is needed? | [[Projects & Learning/HomeLab/Homelab Setup/Status#Active faults\|GPU fault]] |
| T2 | Why is OpenIPMI failed, is usable IPMI hardware present, and is it needed for the hardware readings I want? | [[Projects & Learning/HomeLab/Homelab Setup/Status#Active faults\|IPMI and metric coverage]] |
| T3 | What caused the D1/storage dropouts and the E7450 disconnect during its web-UI update? Establish reboot, host, link, and cluster evidence separately. | [[Projects & Learning/HomeLab/Node Issues/Open Questions\|Node Issues questions]] |
| T4 | What do the SMART baseline/trends mean for disk health, and is any action justified? | [[Projects & Learning/HomeLab/Homelab Setup/Status#Disk and temperature observations\|Disk observations]] |
