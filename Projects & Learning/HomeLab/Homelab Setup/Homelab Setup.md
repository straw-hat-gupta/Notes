# Homelab Setup

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

The maintained home for hardware, storage, networking, configuration, and operational status. Structure established 2026-10-27 at the user's request. Existing inventory is preserved; the other records are ready to fill in as facts are confirmed.

## Records

| Record | Keep here |
| --- | --- |
| [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory|Hardware / Node Inventory]] | Nodes, CPUs, RAM modules and slots, GPUs, NICs, and physical disks |
| [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration|Storage Configuration]] | Boot layout, pools, RAID/ZFS, filesystems, datasets, mounts, shares, and workload storage |
| [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration|Network Configuration]] | Network devices, addresses, interfaces, bridges, VLANs, routing, DNS, and access |
| [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Cluster Configuration|Cluster Configuration]] | Proxmox versions, cluster membership, repositories, passthrough, and host settings |
| [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]] | VM/container placement, allocations, service configuration, and dependencies |
| [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]] | Dated node/service observations, faults, and verified recoveries |
| [[Projects & Learning/HomeLab/Homelab Setup/Change Log|Change Log]] | Confirmed setup changes and their supporting evidence |

## Maintaining these records

Follow [[Projects & Learning/HomeLab/AGENTS|HomeLab agent instructions]]. Keep one authoritative record for each fact and link to it elsewhere. Record the observation date and source when updating a setting or status; distinguish confirmed, reported, historical, conflicting, and unknown details. A documentation update date does not mean the hardware was freshly checked.

Use focused notes within these folders as the setup grows. Add sanitized configuration extracts only when available; never store credentials or private keys. Plans and unchecked tasks do not establish installed configuration or current health.

## Connections

The setup records support [[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]], [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote Development]], and [[Projects & Learning/HomeLab/Project Hosting/Project Hosting|Project Hosting]].

## Tasks

![[Projects & Learning/HomeLab/Homelab Setup/Tasks]]
