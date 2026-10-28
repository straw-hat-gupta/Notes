# Node Inventory

Back to [[Projects & Learning/HomeLab/HomeLab Overview|Homelab]] · [[Projects & Learning/Big Tasks|Big tasks]]

Consolidated hardware and workload record. All details needed from earlier notes are included here. This is documented inventory, not a fresh hardware audit; conflicting records are marked below.

| Node | CPU | RAM | Disks documented | GPU | Known workload / context |
| --- | --- | --- | --- | --- | --- |
| pve-d1 | Intel i7-4790 | 32 GB (4 × 8 GB) | 128 GB SATA SSD for Proxmox; additional SSD listed as 256 GB, with a separate 250 GB entry to reconcile | GTX 1070 family; saved hardware notes say 1070 Ti, but saved PCI output identifies GTX 1070; verify exact card | llm-gpu VM; GPU passthrough; Career Ops; powered on but appearing offline in Proxmox |
| pve-d2 | Intel i7-4790 | 16 GB (2 × 8 GB) | 256 GB SATA SSD for Proxmox | None reported | Workloads to inventory |
| pve-6420 | Intel i5-2520M | 6 GB (2 GB + 4 GB) | 320 GB HDD for Proxmox | None reported | Workloads to inventory |
| pve-7450 | Intel i7-5600U | 16 GB (2 × 8 GB) | 128 GB SATA SSD for Proxmox | None reported | Workloads to inventory |
| pve-storage | Intel i5-3570 | 24 GB | 128 GB SATA SSD for Proxmox; 2 × 1 TB HDD; additional 128 GB SATA SSD | None reported | Reported node issues; workloads to inventory |

## Existing VM record

| VM | Host | Recorded address | Recorded MAC | Current context |
| --- | --- | --- | --- | --- |
| llm-gpu | pve-d1 | 10.44.0.170/24 | bc:24:11:3a:9e:55 | GPU passthrough; Career Ops runs here; possible development workspace |

The VM name describes an existing machine, not a new service to provision. Address and MAC are preserved records, not freshly verified.

## Saved GPU identification

Saved PCI output identifies the graphics device as NVIDIA GP104 GeForce GTX 1070, device ID `10de:1b81`, and its audio function as `10de:10f0`. This explains the model ambiguity in the table; verify against the physical/live card before relying on a precise model.

## Inventory tasks

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] owns the verification and workload-documentation checklist.

![[Projects & Learning/HomeLab/Homelab Setup/Tasks]]

## Connections
- [[Projects & Learning/HomeLab/Node Issues/Node Issues|Node issues]]
- [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote development]] — placement undecided.
- [[Projects & Learning/Projects/Career Ops/Career Ops|Career Ops]] — currently on llm-gpu / pve-d1.
