# Node Inventory

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]] · [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]]

Observed over SSH on 2026-10-27 at 21:37 MDT. Sources: `lscpu`, SMBIOS system/board information, `dmidecode -t 17`, `lsblk`, `lspci -nnk`, and `ethtool`. [[Projects & Learning/HomeLab/Homelab Setup/Evidence/2026-10-27.json|Collected evidence]].

## Nodes

| Node | Dell system | Motherboard / revision | CPU | Cores / threads | Installed RAM |
| --- | --- | --- | --- | --- | --- |
| pve-d1 | OptiPlex 7020 | 0F5C5X / A00 | Intel Core i7-4790 @ 3.60 GHz | 4 / 8 | 32 GB |
| pve-d2 | OptiPlex 7020 | 02YYK5 / A01 | Intel Core i7-4790 @ 3.60 GHz | 4 / 8 | 16 GB |
| pve-storage | OptiPlex 7010 | 0GY6Y8 / A03 | Intel Core i5-3570 @ 3.40 GHz | 4 / 4 | 24 GB |
| pve-6420 | Latitude E6420 | 038C0K / A00 | Intel Core i5-2430M @ 2.40 GHz | 2 / 4 | 6 GB |
| pve-7450 | Latitude E7450 | 06HN6G / A00 | Intel Core i7-5600U @ 2.60 GHz | 2 / 4 | 16 GB |

Total installed RAM: 94 GB. Total CPU capacity: 16 physical cores and 28 hardware threads. All five nodes report one socket, x86-64 architecture, and VT-x.

## RAM slots

All installed modules report DDR3 and 64-bit total/data widths. Speeds below are SMBIOS module speeds. Configured speed also reports 1600 MT/s on all nodes except pve-6420, where that field is unavailable. I use its SMBIOS-reported module speed of 1333 MT/s in this inventory (confirmed 2026-10-27).

### pve-d1

| Slot / bank | Size | Form factor | Speed | Manufacturer | Part number |
| --- | --- | --- | --- | --- | --- |
| DIMM1 | 8 GB | DIMM | 1600 MT/s | Hynix/Hyundai | HMT41GU6BFR8C-PB |
| DIMM2 | 8 GB | DIMM | 1600 MT/s | Hynix/Hyundai | HMT41GU6BFR8C-PB |
| DIMM3 | 8 GB | DIMM | 1600 MT/s | Hynix/Hyundai | HMT41GU6BFR8C-PB |
| DIMM4 | 8 GB | DIMM | 1600 MT/s | Hynix/Hyundai | HMT41GU6BFR8A-PB |

### pve-d2

| Slot / bank | Size | Form factor | Speed | Manufacturer | Part number |
| --- | --- | --- | --- | --- | --- |
| DIMM1 | 8 GB | DIMM | 1600 MT/s | Hynix/Hyundai | HMT41GU6BFR8C-PB |
| DIMM2 | 8 GB | DIMM | 1600 MT/s | Hynix/Hyundai | HMT41GU6BFR8A-PB |
| DIMM3 | Empty | DIMM | — | — | — |
| DIMM4 | Empty | DIMM | — | — | — |

### pve-storage

| Slot / bank | Size | Form factor | Speed | Manufacturer | Part number |
| --- | --- | --- | --- | --- | --- |
| DIMM1 | 4 GB | DIMM | 1600 MT/s | Hynix/Hyundai | HMT451U6AFR8C-PB |
| DIMM2 | 4 GB | DIMM | 1600 MT/s | Hynix/Hyundai | HMT451U6AFR8C-PB |
| DIMM3 | 8 GB | DIMM | 1600 MT/s | SMBIOS code 04CD | F3-1600C11-8GNT |
| DIMM4 | 8 GB | DIMM | 1600 MT/s | SMBIOS code 04CD | F3-1600C11-8GNT |

### pve-6420

| Slot / bank | Size | Form factor | Speed | Manufacturer | Part number |
| --- | --- | --- | --- | --- | --- |
| ChannelA-DIMM0 / BANK 0 | 2 GB | SODIMM | 1333 MT/s | Hynix/Hyundai | HMT325S6CFR8C-H9 |
| ChannelB-DIMM0 / BANK 2 | 4 GB | SODIMM | 1333 MT/s | Samsung | M471B5173DB0-YK0 |

### pve-7450

| Slot / bank | Size | Form factor | Speed | Manufacturer | Part number |
| --- | --- | --- | --- | --- | --- |
| DIMM A | 8 GB | SODIMM | 1600 MT/s | Micron | 16KTF1G64HZ-1G6N1 |
| DIMM B | 8 GB | SODIMM | 1600 MT/s | Micron | 16KTF1G64HZ-1G6N1 |

## Physical disks

Device paths are the names observed at collection time. Capacities are decimal GB with exact byte counts from `lsblk`; pool sizes, partitions, mounts, and disk assignments are in [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration|Storage Configuration]].

| Node | Device | Model | Type / transport | Capacity | Bytes |
| --- | --- | --- | --- | --- | --- |
| pve-d1 | /dev/sda | Samsung SSD 850 EVO 250GB | SSD / SATA | 250 GB | 250,059,350,016 |
| pve-d1 | /dev/sdb | TOSHIBA THNSNK128GCS8 SATA 128GB | SSD / SATA | 128 GB | 128,035,676,160 |
| pve-d2 | /dev/sda | LITEONIT LCS-256L9S-11 2.5 7mm 256GB | SSD / SATA | 256 GB | 256,060,514,304 |
| pve-storage | /dev/sda | ST1000DM003-1ER162 | HDD / SATA | 1,000 GB | 1,000,204,886,016 |
| pve-storage | /dev/sdb | WDC WD10EZEX-00WN4A0 | HDD / SATA | 1,000 GB | 1,000,204,886,016 |
| pve-storage | /dev/sdc | SAMSUNG SSD PM871 2.5 7mm 128GB | SSD / SATA | 128 GB | 128,035,676,160 |
| pve-storage | /dev/sdd | SanDisk X300 2.5 7MM 128GB | SSD / SATA | 128 GB | 128,035,676,160 |
| pve-6420 | /dev/sda | WDC WD3200BEKT-75PVMT1 | HDD / SATA | 320 GB | 320,072,933,376 |
| pve-7450 | /dev/sda | SAMSUNG SSD PM851 mSATA 128GB | SSD / SATA | 128 GB | 128,035,676,160 |

## Graphics devices

PCI names and subsystem identifications from `lspci -nnk`:

| Node | PCI address | Device | PCI ID | Subsystem identification | Host driver |
| --- | --- | --- | --- | --- | --- |
| pve-d1 | 01:00.0 | NVIDIA GP104 GeForce GTX 1070 | 10de:1b81 | ASUSTeK 1043:8599 | vfio-pci |
| pve-d1 | 05:00.0 | AMD Caicos XT | 1002:6778 | Dell Radeon HD 7470, 1028:2120 | radeon |
| pve-d2 | 01:00.0 | AMD Oland | 1002:6611 | Dell Radeon R5 240 OEM, 1028:210b | amdgpu |
| pve-storage | 02:00.0 | AMD Oland | 1002:6611 | Dell Radeon R5 240 OEM, 1028:210b | amdgpu |
| pve-6420 | 00:02.0 | Intel 2nd Generation Core integrated graphics | 8086:0116 | Dell 1028:0493 | i915 |
| pve-6420 | 01:00.0 | NVIDIA GF119M NVS 4200M | 10de:1056 | Dell 1028:1493 | nouveau |
| pve-7450 | 00:02.0 | Intel HD Graphics 5500 | 8086:1616 | Dell 1028:062e | i915 |

My D1 card is an ASUS ROG Strix GTX 1070 with 8 GB VRAM. Confirmed 2026-10-27. Recording other display-card VRAM is deferred unless a workload needs it (confirmed 2026-10-28).

The GTX 1070 audio function is `01:00.1`, PCI ID `10de:10f0`, also bound to `vfio-pci`. GPU passthrough settings and guest allocation are in [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]].

## Network adapters

| Node | PCI address | Adapter | PCI ID | Host driver |
| --- | --- | --- | --- | --- |
| pve-d1 | 00:19.0 | Intel Ethernet Connection I217-LM | 8086:153a | e1000e |
| pve-d2 | 00:19.0 | Intel Ethernet Connection I217-LM | 8086:153a | e1000e |
| pve-storage | 00:19.0 | Intel 82579LM Gigabit Network Connection | 8086:1502 | e1000e |
| pve-6420 | 00:19.0 | Intel 82579LM Gigabit Network Connection | 8086:1502 | e1000e |
| pve-6420 | 03:00.0 | Broadcom BCM43228 802.11a/b/g/n; Dell Wireless 1530 subsystem | 14e4:4359 | bcma-pci-bridge |
| pve-7450 | 00:19.0 | Intel Ethernet Connection (3) I218-LM | 8086:15a2 | e1000e |
| pve-7450 | 02:00.0 | Intel Wireless 7265; Dual Band Wireless-AC 7265 subsystem | 8086:095a | iwlwifi |

Interface names, bridge membership, addresses, and negotiated links are in [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration|Network Configuration]]. The purchased replacement NICs are listed below.

## Replacement NICs

Both cards are purchased and **not installed** (confirmed 2026-10-28). They are intended for pve-d1 and pve-storage only if diagnosis confirms a NIC problem. The card-to-host assignment is not selected.

| Model | Controller recorded in my answer | Connection |
| --- | --- | --- |
| [StarTech ST1000SPEXI](https://retail.era.ca/collections/networking-components/products/startech-com-st1000spexi-1-port-gigabit-ethernet-pcie-network-adapter-card) | Intel I210 | PCIe x1, one 1 Gb/s RJ45 port |
| [Intel Gigabit CT EXPI9301CTBLK](https://retail.era.ca/collections/networking-components/products/intel-gigabit-ct-desktop-adapter-expi9301ctblk-pcie-x1-nic) | Intel 82574L | PCIe x1, one 1 Gb/s RJ45 port |

Saved listing details, recorded 2026-10-27: both used and described as tested, listed at $17.50 each.
