# Node Inventory

Back to [[Projects & Learning/HomeLab/HomeLab Overview|Homelab]] · [[Projects & Learning/Big Tasks|Big tasks]]

Hardware copied from [[HomeLab/Compute Cluster Hardware]]. This is an initial documented inventory, not a fresh hardware audit. Workload details also include the 2026-10-27 brain dump.

| Node | CPU | RAM | Disks documented | GPU | Known workload / context |
| --- | --- | --- | --- | --- | --- |
| pve-d1 | Intel i7-4790 | 32 GB (4 × 8 GB) | 128 GB SATA SSD for Proxmox; additional SSD listed as 256 GB, with a separate 250 GB entry to reconcile | NVIDIA GTX 1070 Ti per source; exact model to verify | llm-gpu VM; GPU passthrough; Career Ops; reported node issues |
| pve-d2 | Intel i7-4790 | 16 GB (2 × 8 GB) | 256 GB SATA SSD for Proxmox | None reported | Workloads to inventory |
| pve-6420 | Intel i5-2520M | 6 GB (2 GB + 4 GB) | 320 GB HDD for Proxmox | None reported | Workloads to inventory |
| pve-7450 | Intel i7-5600U | 16 GB (2 × 8 GB) | 128 GB SATA SSD for Proxmox | None reported | Workloads to inventory |
| pve-storage | Intel i5-3570 | 24 GB | 128 GB SATA SSD for Proxmox; 2 × 1 TB HDD; additional 128 GB SATA SSD | None reported | Reported node issues; workloads to inventory |

## Inventory follow-up
- [ ] Verify hardware against live nodes, including pve-d1 GPU and SSD details.
- [ ] Record current VM/container placement and purpose on each node.
- [ ] Record storage layout and network hardware where relevant.

## Connections
- [[Projects & Learning/HomeLab/Node Issues/Node Issues|Node issues]]
- [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote development]] — placement undecided.
- [[Projects & Learning/Projects/Career Ops/Career Ops|Career Ops]] — currently on llm-gpu / pve-d1.
