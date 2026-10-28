# HomeLab

[[Projects & Learning/Start Here|Start Here]] · [[Projects & Learning/Big Tasks|Big Tasks]]

Five Proxmox nodes: pve-d1, pve-d2, pve-6420, pve-7450, and pve-storage.

For agents editing this area: [[Projects & Learning/HomeLab/AGENTS|HomeLab agent instructions]].

## Work areas

| Folder | Outcome |
| --- | --- |
| [[Projects & Learning/HomeLab/Monitoring/Monitoring\|Monitoring]] | Review load/temperature coverage and useful benchmark/history features |
| [[Projects & Learning/HomeLab/Node Issues/Node Issues\|Node Issues]] | Diagnose pve-d1 and pve-storage appearing offline while still powered on |
| [[Projects & Learning/HomeLab/Remote Development/Remote Development\|Remote Development]] | Keep development and long-running agents on a homelab VM |
| [[Projects & Learning/HomeLab/Agent Access/Agent Access\|Agent Access]] | Reach homelab tools through an agent in the ChatGPT desktop app |
| [[Projects & Learning/HomeLab/Shared MCP Servers/Shared MCP Servers\|Shared MCP Servers]] | Share cluster-hosted tools across multiple agents |
| [[Projects & Learning/HomeLab/Project Hosting/Project Hosting\|Project Hosting]] | Connect domain/subdomains to demos and personal services |
| [[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup\|Homelab Setup]] | Maintain current hardware, configuration, workloads, and operational status |

## Current setup

[[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory|Hardware]] holds the live node inventory. [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]] records VM 301, LXC 100/101/201, service endpoints, and resource allocations.

D1 has the GTX 1070 assigned to llm-gpu; the other installed graphics devices are listed in the hardware record. Current health and faults are in [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]].

## Current direction

My 2026-10-27 answers are in [[Projects & Learning/HomeLab/ANSWERS|ANSWERS]]. I want TrueNAS/shared storage on pve-storage, aligned host versions, a clearer cluster dashboard, and portable services that recover on another node after a host failure. The setup records distinguish these plans from the installed configuration.

## Open questions

[[Projects & Learning/HomeLab/Homelab Setup/Open Questions|Setup questions]] covers hardware, storage, networking, configuration, and status. Each related work area keeps its own Open Questions note, linked from its overview.
