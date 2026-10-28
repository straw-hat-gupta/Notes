# HomeLab

[[Projects & Learning/Start Here|Start Here]] · [[Projects & Learning/Big Tasks|Big Tasks]]

Five Proxmox nodes: pve-d1, pve-d2, pve-6420, pve-7450, and pve-storage.

For agents editing this area: [[Projects & Learning/HomeLab/AGENTS|HomeLab agent instructions]].

## Work areas

| Folder | Outcome |
| --- | --- |
| [[Projects & Learning/HomeLab/Monitoring/Monitoring\|Monitoring]] | Review load/temperature coverage and useful benchmark/history features |
| [[Projects & Learning/HomeLab/Node Issues/Node Issues\|Node Issues]] | Diagnose D1/storage dropouts and the E7450 disconnect during an update |
| [[Projects & Learning/HomeLab/Remote Development/Remote Development\|Remote Development]] | Keep development and long-running agents on a homelab VM |
| [[Projects & Learning/HomeLab/Agent Access/Agent Access\|Agent Access]] | Reach homelab tools through an agent in the ChatGPT desktop app |
| [[Projects & Learning/HomeLab/Shared MCP Servers/Shared MCP Servers\|Shared MCP Servers]] | Share cluster-hosted tools across multiple agents |
| [[Projects & Learning/HomeLab/Project Hosting/Project Hosting\|Project Hosting]] | Connect domain/subdomains to demos and personal services |
| [[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup\|Homelab Setup]] | Maintain current hardware, configuration, workloads, and operational status |

## Current setup

[[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory|Hardware]] holds the live node inventory. [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]] records VM 301, LXC 100/101/201, service endpoints, and resource allocations.

D1 has the GTX 1070 assigned to llm-gpu; the other installed graphics devices are listed in the hardware record. Current health and faults are in [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]].

## Current direction

The next step is a diagnosis plan for the reported host disconnects, GPU driver failure, OpenIPMI failures, and disk-health questions. The issue register is in [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]].

All five nodes have been updated by my report on 2026-10-28; their current versions/running kernels still need verification. Longer-term work remains TrueNAS/shared storage, foundational metric access before choosing a dashboard stack, Career Ops backup and a dedicated LXC/container, and request-based service provisioning/recovery.

## Open questions

[[Projects & Learning/HomeLab/Homelab Setup/Open Questions|Setup questions]] covers hardware, storage, networking, configuration, and status. Each related work area keeps its own Open Questions note, linked from its overview.
