# Storage Configuration

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|Storage questions]]

Checked 2026-10-27, 21:37 MDT. Capacities below use GiB (1 GiB = 1,073,741,824 bytes).

## Storage layout

All configured Proxmox storage is local to its node. Each host boots from a single disk containing the `pve` volume group, root filesystem, swap, and the `data` thin pool. `pve-d1` also has a separate disk and thin pool for VM 301. There is no disk redundancy in these configured LVM layouts. No Linux MD RAID arrays were listed in `/proc/mdstat` on any node.

| Storage ID | Type | Backing / location | Nodes | Allowed content |
| --- | --- | --- | --- | --- |
| `local` | Directory | `/var/lib/vz`, on the host root filesystem | All five nodes, separate storage on each | ISO images, container templates, import files, backups |
| `local-lvm` | LVM-thin | VG `pve`, thin pool `data`, on the boot disk | All five nodes, separate pools on each | VM disks and container root disks |
| `d1-ssd-lvm` | LVM-thin | VG and thin pool `d1-ssd-lvm`, `/dev/sda` | `pve-d1` only | VM disks and container root disks |

No ZFS pools or datasets were listed on any node. No shared, NFS, SMB/CIFS, Ceph, or Proxmox Backup Server storage is configured in the Proxmox storage list.

## Boot disks, filesystems, and LVM

Physical disk models and nominal capacities are in [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Physical disks|Node Inventory]]. Device paths below describe the current mapping.

| Node | Boot disk / LVM PV | Root LV allocation (GiB) | Root filesystem / mount | Swap LV (GiB) | `pve` VG free (GiB) | Mounted EFI partition |
| --- | --- | --- | --- | --- | --- | --- |
| pve-d1 | `/dev/sdb` / `/dev/sdb3` | 39.56 | ext4, `/` | 8.00 | 14.75 | Not mounted at observation |
| pve-d2 | `/dev/sda` / `/dev/sda3` | 69.37 | ext4, `/` | 8.00 | 16.00 | Not mounted at observation |
| pve-storage | `/dev/sdc` / `/dev/sdc3` | 39.62 | ext4, `/` | 7.74 | 14.75 | /dev/sdc2 |
| pve-6420 | `/dev/sda` / `/dev/sda3` | 84.86 | ext4, `/` | 5.67 | 16.00 | Not mounted at observation |
| pve-7450 | `/dev/sda` / `/dev/sda3` | 39.50 | xfs, `/` | 8.00 | 14.63 | /dev/sda2 |

`local` shares capacity with the host OS; its capacity is not additional to the root filesystem. Root LV allocation is larger than usable filesystem capacity. LVM VG free space is separate from free space within a thin pool or filesystem.

## Capacity at observation

| Node | Storage ID | Capacity (GiB) | Used (GiB) | Available (GiB) | Thin-pool data used | Thin-pool metadata used |
| --- | --- | --- | --- | --- | --- | --- |
| pve-d1 | `local` | 38.64 | 14.48 | 22.16 | — | — |
| pve-d1 | `local-lvm` | 53.93 | 0.00 | 53.93 | 0.00% | 1.59% |
| pve-d1 | `d1-ssd-lvm` | 228.11 | 67.27 | 160.84 | 29.49% | 1.73% |
| pve-d2 | `local` | 67.73 | 14.05 | 50.19 | — | — |
| pve-d2 | `local-lvm` | 141.23 | 9.34 | 131.89 | 6.61% | 1.35% |
| pve-storage | `local` | 38.70 | 12.15 | 24.56 | — | — |
| pve-storage | `local-lvm` | 54.12 | 0.00 | 54.12 | 0.00% | 1.59% |
| pve-6420 | `local` | 82.97 | 12.69 | 66.03 | — | — |
| pve-6420 | `local-lvm` | 186.76 | 24.48 | 162.27 | 13.11% | 1.27% |
| pve-7450 | `local` | 39.43 | 14.04 | 25.39 | — | — |
| pve-7450 | `local-lvm` | 53.87 | 0.00 | 53.87 | 0.00% | 1.59% |

Thin-pool usage measures allocated blocks, rather than the total provisioned size of guest disks. `d1-ssd-lvm` is configured only for `pve-d1`; its unavailable status on other nodes reflects that node restriction.

## Guest disk assignments

| Guest | Host | Volume | Provisioned size | Configuration |
| --- | --- | --- | --- | --- |
| VM 301 `llm-gpu` | pve-d1 | `d1-ssd-lvm:vm-301-disk-1` | 160 GiB | `scsi0`, VirtIO SCSI single, discard enabled, IO thread enabled |
| VM 301 `llm-gpu` | pve-d1 | `d1-ssd-lvm:vm-301-disk-0` | 4 MiB | `efidisk0`, EFI type `4m`, Microsoft 2023 certificate, pre-enrolled keys |
| LXC 100 `app-runner` | pve-d2 | `local-lvm:vm-100-disk-0` | 12 GiB | Root disk, ext4 |
| LXC 101 `cf-tunnel` | pve-d2 | `local-lvm:vm-101-disk-0` | 8 GiB | Root disk, ext4 |
| LXC 201 `monitoring` | pve-6420 | `local-lvm:vm-201-disk-0` | 40 GiB | Root disk, ext4 |

Guest purpose, CPU/RAM allocations, and service configuration are in [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]].

## Storage-node data disks

On `pve-storage`, `/dev/sda` and `/dev/sdb` are the two 1 TB HDDs; `/dev/sdd` is the additional 128 GB SSD. They have no listed filesystem, LVM PV, or mounted path and are not part of the configured Proxmox stores. A read-only signature scan found GPT and protective MBR signatures on `/dev/sda`; none were reported on `/dev/sdb` or `/dev/sdd`. No data needing backup or preservation is reported on these two HDDs or the extra SSD (confirmed 2026-10-28). The boot disk is `/dev/sdc`. Pool creation and installation remain pending configuration work.

The intended layout is recorded under [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Planned TrueNAS setup|Planned TrueNAS setup]]. Deployment, SSD allocation, and share choices remain in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|Storage questions]].

## Backups, replication, and shares

| Item | Recorded state |
| --- | --- |
| Scheduled Proxmox backup jobs | None configured (`/cluster/backup` returned an empty list) |
| Proxmox replication jobs | None configured (`/cluster/replication` returned an empty list) |
| Backup-capable storage | `local` on each node allows backup content under `/var/lib/vz` |
| Local Proxmox backup content | No backup entries returned from `local` on any of the five nodes |
| Available Proxmox backup task history | No `vzdump` tasks returned from any of the five node task queries (limit 20) |
| Overall backup coverage | No backups have been established (confirmed 2026-10-27) |
| Retention, offsite copies, and restore testing | Not established; [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage\|backup design remains open]] |
| Host-level shares / external storage clients | None in use (confirmed 2026-10-27) |

## Immediate backup scope

Career Ops on llm-gpu is the current backup priority. I want the complete Career Ops installation, configuration, and persistent state protected before its planned move to a dedicated LXC/container. Exact paths, application-consistent backup steps, schedule, retention, destination, and restore procedure still need to be inventoried and chosen. Confirmed 2026-10-28.

Backup coverage is not established by choosing this scope. The pending work is in [[Projects & Learning/HomeLab/Homelab Setup/Tasks|Tasks]], with destination/design questions in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|Storage questions]].

## Planned TrueNAS setup

I want TrueNAS on pve-storage, with the two 1 TB HDDs in a ZFS stripe for combined capacity. This is a plan; TrueNAS and the pool are not installed. Confirmed 2026-10-27.

| Item | Planned use / decision |
| --- | --- |
| Two 1 TB HDDs | ZFS stripe, no mirror; approximately 2 TB decimal raw capacity before filesystem overhead |
| Shared storage | Backups, Linux ISOs, and data shared by other nodes |
| Network drive | Desired if practical; protocol and client access remain to choose |
| Extra 128 GB SSD | Proposed dedicated TrueNAS boot device; not yet selected or configured |
| Deployment | VM versus bare-metal installation remains undecided |

The spare SSD is a sensible boot-device candidate because TrueNAS separates boot from data storage and specifies an SSD boot device of at least 20 GB. If I retain Proxmox, its current boot SSD must remain separate from the TrueNAS installation. Virtualized TrueNAS also needs a deliberate physical-disk/controller access plan; its hardware guide cautions against virtual data disks for critical storage. This is a proposal pending the deployment decision. [TrueNAS hardware guide](https://www.truenas.com/docs/scale/gettingstarted/tnhardwareguide/).

A stripe has no disk redundancy: losing either data disk can lose the pool. Backups stored only on that pool cannot protect the pool's own data, so backup design must include an independent copy. [TrueNAS pool layouts](https://www.truenas.com/docs/scale/storage/pools/poolcreationwizardscreen/).

I need the TrueNAS VM/bare-metal tradeoffs explained for this hardware before choosing a deployment. Dataset, share-protocol, and permission recommendations should follow the intended clients and uses. These decisions, SSD assignment, and backup destinations are centralized in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|Storage questions]] (confirmed 2026-10-28).

## Sources

`pvesh get /storage`, per-node `/storage` results, `lsblk`, `pvs`, `vgs`, `lvs`, `findmnt`, `qm config`, `pct config`, `zpool list`, `zfs list`, `/proc/mdstat`, `wipefs --no-act --json`, `/cluster/backup`, `/cluster/replication`, per-node `local` backup-content queries, and per-node `vzdump` task-history queries.

[[Projects & Learning/HomeLab/Homelab Setup/Evidence/2026-10-27.json|2026-10-27 snapshot]]
