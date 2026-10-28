# Cluster Configuration

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Configuration|Open questions]]

Last live baseline: 2026-10-27 (America/Edmonton), before the subsequently reported updates. Sources: `pveversion`, `pvecm status`, `ha-manager status`, APT source files, `lspci -nnk`, `/proc/cmdline`, `/etc/modules`, guest-agent queries, and VM configuration. [[Projects & Learning/HomeLab/Homelab Setup/Evidence/2026-10-27.json|Configuration snapshot]]

## Cluster

| Setting | Value |
| --- | --- |
| Name | `homelab` |
| Corosync configuration version | 9 |
| Transport | `knet` |
| Secure authentication | On |
| Quorum provider | `corosync_votequorum` |
| Configured / observed members | 5 / 5 |
| Votes per node | 1 |
| Expected / total votes | 5 / 5 |
| Quorum threshold | 3 |
| Quorum at verification | Quorate on all five nodes |
| HA manager observation | `quorum OK`; fencing standby, CRM watchdog standby |

## Membership and versions

These are the versions observed on 2026-10-27, before the updates reported on 2026-10-28. Current package versions, running kernels, and any pending reboot requirements have not been rechecked.

| Node | Node ID | Proxmox VE manager | Running kernel |
| --- | --- | --- | --- |
| pve-d1 | `0x00000001` | 9.2.3 (`d0fde103346cf89a`) | `7.0.2-7-pve` |
| pve-d2 | `0x00000002` | 9.2.3 (`d0fde103346cf89a`) | `7.0.2-7-pve` |
| pve-7450 | `0x00000003` | 9.2.11 (`f6997e698c7933ea`) | `7.0.14-12-pve` |
| pve-storage | `0x00000004` | 9.2.11 (`f6997e698c7933ea`) | `7.0.14-12-pve` |
| pve-6420 | `0x00000005` | 9.2.11 (`f6997e698c7933ea`) | `7.0.14-12-pve` |

Management addresses and bridge configuration are in [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration|Network Configuration]]. Current observations and faults are in [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]].

## Host updates and version alignment

I updated all five nodes (confirmed 2026-10-28). Completion of those updates is recorded; package/kernel alignment and reboot state still need live verification. I still want a consistent supported baseline and a repeatable maintenance approach.

During the pve-7450 update through the Proxmox web Updates tab, it disconnected from the cluster. I did not initiate a reboot. Whether it rebooted automatically, lost network access, or lost cluster membership has not been established. The incident record is in [[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]], and verification/diagnosis work is in [[Projects & Learning/HomeLab/Homelab Setup/Tasks|Tasks]].

## Package repositories

These source settings are present on all five nodes:

| Source file | URI / suite | Components | State |
| --- | --- | --- | --- |
| `/etc/apt/sources.list.d/debian.sources` | `http://deb.debian.org/debian/` — `trixie`, `trixie-updates` | `main contrib non-free-firmware` | Enabled |
| `/etc/apt/sources.list.d/debian.sources` | `http://security.debian.org/debian-security/` — `trixie-security` | `main contrib non-free-firmware` | Enabled |
| `/etc/apt/sources.list.d/proxmox.sources` | `http://download.proxmox.com/debian/pve` — `trixie` | `pve-no-subscription` | Enabled |
| `/etc/apt/sources.list.d/pve-enterprise.sources` | `https://enterprise.proxmox.com/debian/pve` — `trixie` | `pve-enterprise` | Disabled (`Enabled: false`) |
| `/etc/apt/sources.list.d/ceph.sources` | `https://enterprise.proxmox.com/debian/ceph-squid` — `trixie` | `enterprise` | Disabled (`Enabled: false`) |

`pve-d2` also has `/etc/apt/sources.list.d/tailscale.list`: `https://pkgs.tailscale.com/stable/debian`, suite `trixie`, component `main`, signed by `/usr/share/keyrings/tailscale-archive-keyring.gpg`.

## Host settings

All five hosts use timezone `America/Edmonton` and report NTP synchronization. `pve-cluster`, `corosync`, `pvedaemon`, `pveproxy`, `pvestatd`, `ssh`, and `prometheus-node-exporter` were active at verification.

## GPU passthrough

VM 301 (`llm-gpu`) on `pve-d1` has `hostpci0: 0000:01:00`. Its NVIDIA GTX 1070 display function (`01:00.0`, `10de:1b81`) and audio function (`01:00.1`, `10de:10f0`) are bound to `vfio-pci` on the host.

`pve-d1` boots with `intel_iommu=on iommu=pt` in `/proc/cmdline`. `/etc/modules` lists `vfio`, `vfio_iommu_type1`, and `vfio_pci`.

| VM 301 setting | Value |
| --- | --- |
| BIOS | OVMF |
| Machine | `q35` |
| CPU type | `x86-64-v2-AES` |
| SCSI controller | `virtio-scsi-single` |
| Guest agent | Enabled (`agent: 1`); responds to queries |
| Ballooning | Disabled (`balloon: 0`) |
| NUMA | Disabled (`numa: 0`) |
| EFI disk | `d1-ssd-lvm:vm-301-disk-0`, 4 MiB |

Hardware identification is in [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory|Node Inventory]], and guest allocations are in [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]]. Remaining host-setting questions are in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Configuration|Open Questions]].
