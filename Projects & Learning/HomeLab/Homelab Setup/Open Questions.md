# Homelab Setup — Open Questions

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]]

Open as of 2026-10-27. Confirmed facts and plans are in the linked records; actionable work is in [[Projects & Learning/HomeLab/Homelab Setup/Tasks|Tasks]].

## Hardware

| ID | Question | Relevant record |
| --- | --- | --- |
| H1 | Have either of the purchased StarTech ST1000SPEXI / Intel EXPI9301CTBLK cards been installed, and on which host? | [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Replacement NICs\|Replacement NICs]] |
| H3 | What are the memory capacities of the other discrete graphics cards? D1's ASUS ROG Strix GTX 1070 is confirmed as 8 GB. | [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Graphics devices\|Graphics devices]] |

## Storage

| ID | Question | Relevant record |
| --- | --- | --- |
| S1 | What data needs backup, on what schedule, with what retention and independent/offsite destination? No backups are established. | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Backups, replication, and shares\|Backups]] |
| S2 | Is there any existing data to preserve on the two HDDs or spare SSD before building the planned pool? | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Storage-node data disks\|Data disks]] |
| S4 | Should TrueNAS run as a VM or bare metal, and can the spare 128 GB SSD be dedicated to its boot device? If virtualized, how will it access the physical data disks/controller? | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Planned TrueNAS setup\|TrueNAS plan]] |
| S5 | Which datasets, share protocols, clients, and permissions are needed for backups, Linux ISOs, shared data, and a network drive? | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Planned TrueNAS setup\|Shared-storage plan]] |

## Networking

| ID | Question | Relevant record |
| --- | --- | --- |
| N1 | What are the exact router/switch models, port assignments, DHCP scope, and guest reservations? The five Proxmox hosts are static and each uses an Ethernet cable to the TP-Link 8-port switch. | [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration\|Networking]] |
| N2 | Is pve-7450's unused nic1 entry accidental, and can it be removed after checking dependencies? | [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Other interfaces\|Other interfaces]] |
| N3 | Which effective default firewall/Tailscale rules apply, and which remote-access boundaries should be configured? Tailscale is installed on D2 and llm-gpu; no custom rules have been set up. | [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Firewall\|Firewall and access]] |
| N4 | Cloudflare record/route inventory and public/private access choices. | [[Projects & Learning/HomeLab/Project Hosting/Open Questions\|Project Hosting questions]] |

## Configuration

| ID | Question | Relevant record |
| --- | --- | --- |
| C1 | Which supported Proxmox/kernel baseline and maintenance sequence should be used to align all five nodes? Alignment is the intended outcome; updates are not done. | [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Cluster Configuration#Planned version alignment\|Version alignment]] |
| C2 | What Career Ops process, configuration, and persistent data need moving from llm-gpu? Its current access is through that machine; portable hosting and recovery are planned. | [[Projects & Learning/HomeLab/Project Hosting/Open Questions\|Service-hosting questions]] |
| C3 | Monitoring stack choice, dashboard panels, retention, and alerting. | [[Projects & Learning/HomeLab/Monitoring/Open Questions\|Monitoring questions]] |

## Status

| ID | Question | Relevant record |
| --- | --- | --- |
| T1 | Why does nvidia-smi fail in llm-gpu, and what repair is needed? | [[Projects & Learning/HomeLab/Homelab Setup/Status#Active faults\|GPU fault]] |
| T2 | Why is openipmi.service failed, do these machines have usable IPMI hardware, and is the service needed? | [[Projects & Learning/HomeLab/Homelab Setup/Status#Active faults\|IPMI fault and context]] |
| T3 | What caused the D1/storage dropouts, including any BIOS/firmware, host, link, or cluster evidence? | [[Projects & Learning/HomeLab/Node Issues/Open Questions\|Node Issues questions]] |
| T4 | Are the SMART values stable, and do their vendor-specific meanings indicate any actionable disk problem? | [[Projects & Learning/HomeLab/Homelab Setup/Status#Disk and temperature observations\|Disk observations]] |
