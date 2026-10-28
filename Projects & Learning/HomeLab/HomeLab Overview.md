# HomeLab

[[Projects & Learning/Start Here|Start Here]] · [[Projects & Learning/Big Tasks|Big Tasks]]

Five Proxmox nodes: pve-d1, pve-d2, pve-6420, pve-7450, and pve-storage.

## Work areas

| Folder | Outcome |
| --- | --- |
| [[Projects & Learning/HomeLab/Monitoring/Monitoring|Monitoring]] | Review load/temperature coverage and useful benchmark/history features |
| [[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]] | Diagnose pve-d1 and pve-storage appearing offline while still powered on |
| [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote Development]] | Keep development and long-running agents on a homelab VM |
| [[Projects & Learning/HomeLab/Agent Access/Agent Access|Agent Access]] | Reach homelab tools through an agent in the ChatGPT desktop app |
| [[Projects & Learning/HomeLab/Shared MCP Servers/Shared MCP Servers|Shared MCP Servers]] | Share cluster-hosted tools across multiple agents |
| [[Projects & Learning/HomeLab/Project Hosting/Project Hosting|Project Hosting]] | Connect domain/subdomains to demos and personal services |
| [[Projects & Learning/HomeLab/Hardware Inventory/Hardware Inventory|Hardware Inventory]] | Maintain the five-node hardware and workload record |

## Current workload context

[[Projects & Learning/HomeLab/Node Inventory|Node Inventory]] holds the hardware details. The llm-gpu VM runs on pve-d1 with GPU passthrough and hosts [[Projects & Learning/Projects/Career Ops/Career Ops|Career Ops]]. Per the brain dump, pve-d1 is the only GPU node. The future development workspace may reuse llm-gpu or use another VM; no placement decision has been made.

## Preserved operational context

Hardware details, conflicting GPU records, and the existing VM address are included in [[Projects & Learning/HomeLab/Node Inventory|Node Inventory]]. Desired dashboard and benchmark features are recorded in [[Projects & Learning/HomeLab/Monitoring/Monitoring|Monitoring]]. Earlier remote-access and management-skill goals are included in their respective task folders.
