# Homelab Setup — Open Questions

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]]

Open as of 2026-10-27. Confirmed answers belong in the linked setup record; investigation checklists belong in [[Projects & Learning/HomeLab/Homelab Setup/Tasks|Tasks]].

## Hardware

| ID  | Question                                                                                                                                                      | Relevant record                                                                      |                    |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------------ |
| H1  | What are the models of the two purchased replacement NICs, and are either installed? The hosts currently use their onboard Intel wired NICs.                  | [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Network adapters | Network adapters]] |
| H2  | What is pve-6420's actual configured RAM speed? SMBIOS lists 1333 MT/s module speed without a configured-speed field.                                         | [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#RAM slots        | RAM slots]]        |
| H3  | What VRAM capacities should be recorded for the graphics devices? Current PCI identification does not establish VRAM, and the VM's NVIDIA driver query fails. | [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Graphics devices | Graphics devices]] |
|     |                                                                                                                                                               |                                                                                      |                    |

## Storage

| ID | Question | Relevant record |
| --- | --- | --- |
| S1 | Are there manual or external backups? What are the retention, offsite copy, and last successful restore test? There are no configured Proxmox backup jobs or listed local backup entries. | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Backups, replication, and shares|Backups]] |
| S2 | What data needs preserving on pve-storage's two HDDs and extra SSD, and what layout is intended? The first HDD still has GPT/PMBR signatures. | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Storage-node data disks|Data disks]] |
| S3 | Are any host-level shares or external storage clients in use outside Proxmox's storage list? | [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Backups, replication, and shares|Shares]] |

## Networking

| ID | Question | Relevant record |
| --- | --- | --- |
| N1 | What router/switch models, ports, cabling, DHCP scope, and reservations are in use? Guest DHCP addresses are observed leases, not confirmed reservations. | [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration|Networking]] |
| N2 | Why is nic1 configured on pve-7450 when no live nic1 device is present? | [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Other interfaces|Other interfaces]] |
| N3 | What firewall rules, router exposure, and Tailscale ACLs/routes define access? Proxmox firewall reports disabled on all hosts. | [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Firewall|Firewall]] |
| N4 | Which public hostnames and origins does the running Cloudflare tunnel serve? | [[Projects & Learning/HomeLab/Project Hosting/Open Questions|Project Hosting questions]] |

## Configuration

| ID | Question | Relevant record |
| --- | --- | --- |
| C1 | Should host Proxmox/kernel versions be aligned? D1/D2 and the other three hosts currently run different versions. | [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Cluster Configuration#Membership and versions|Versions]] |
| C2 | What is the current Career Ops process, configuration location, and intended endpoint on llm-gpu? Earlier notes place it there; a running application endpoint has not been established. | [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services#Services|Services]] |
| C3 | What Alertmanager notification routes, Prometheus retention, and Grafana dashboard exports should be recorded? Credential-bearing configuration files were excluded from the snapshot. | [[Projects & Learning/HomeLab/Monitoring/Open Questions|Monitoring questions]] |

## Status

| ID | Question | Relevant record |
| --- | --- | --- |
| T1 | Why can nvidia-smi in llm-gpu not communicate with the NVIDIA driver although the GTX 1070 is visible in the VM? | [[Projects & Learning/HomeLab/Homelab Setup/Status#Active faults|Active faults]] |
| T2 | Why is openipmi.service failed on all five hosts, and is IPMI functionality needed on these systems? | [[Projects & Learning/HomeLab/Homelab Setup/Status#Active faults|Active faults]] |
| T3 | What caused the earlier D1/storage dropouts, and have they stopped recurring? A reachable snapshot does not establish a lasting fix. | [[Projects & Learning/HomeLab/Node Issues/Open Questions|Node Issues questions]] |
| T4 | Are SMART attributes stable over time, particularly the Samsung SSD raw attribute 5 values? Vendor-specific raw values alone do not establish failing sectors. | [[Projects & Learning/HomeLab/Homelab Setup/Status#Disk and temperature observations|Disk observations]] |
