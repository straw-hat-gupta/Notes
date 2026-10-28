# Network Configuration

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|Open questions]]

Verified 2026-10-27 (America/Edmonton). Sources: Proxmox network configuration, `ip addr`, `ip route`, `ethtool`, guest configuration, QEMU guest agent, VM netplan (`dhcp4: true`), `pve-firewall status`, and `/etc/resolv.conf`. [[Projects & Learning/HomeLab/Homelab Setup/Evidence/2026-10-27.json|Configuration snapshot]]

## LAN

| Setting | Value |
| --- | --- |
| Management / guest LAN | `10.44.0.0/24` |
| Default gateway | `10.44.0.1` |
| Host DNS server | `10.44.0.1` |
| Host DNS search domain | `home.arpa` |
| Host bridge | `vmbr0` |
| Physical uplink | `nic0` (`enp0s25` alternate name) |
| Bridge and uplink MTU | 1500 |
| Negotiated wired links | 1 Gb/s, full duplex, auto-negotiation enabled |

Each host has a static address on `vmbr0`. The physical `nic0` interface is a bridge port without its own IP address. `vmbr0` starts automatically; STP is off and forwarding delay is 0.

## Host connections

| Node | Management address | Uplink MAC | Bridge / uplink | Link at verification |
| --- | --- | --- | --- | --- |
| pve-d1 | `10.44.0.50/24` | `64:00:6a:4f:c9:55` | `vmbr0` / `nic0` | Up |
| pve-d2 | `10.44.0.51/24` | `64:00:6a:53:70:5f` | `vmbr0` / `nic0` | Up |
| pve-6420 | `10.44.0.52/24` | `d4:be:d9:29:7e:7c` | `vmbr0` / `nic0` | Up |
| pve-7450 | `10.44.0.53/24` | `20:47:47:bf:f2:e0` | `vmbr0` / `nic0` | Up |
| pve-storage | `10.44.0.54/24` | `34:17:eb:bc:35:68` | `vmbr0` / `nic0` | Up |

The wired adapters and driver details are in [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Network adapters|Node Inventory]].

## Guest connections

| Guest | Host | Guest interface / model | Bridge | Address configuration | MAC | Proxmox NIC firewall flag |
| --- | --- | --- | --- | --- | --- | --- |
| 100 — app-runner | pve-d2 | `eth0` / veth | `vmbr0` | `10.44.0.220/24` via DHCP | `BC:24:11:BF:BD:11` | Not specified |
| 101 — cf-tunnel | pve-d2 | `eth0` / veth | `vmbr0` | `10.44.0.76/24` via DHCP; IPv6 DHCP configured | `BC:24:11:A3:57:77` | Enabled |
| 201 — monitoring | pve-6420 | `eth0` / veth | `vmbr0` | `10.44.0.80/24`; gateway `10.44.0.1`; IPv6 auto | `BC:24:11:4B:F3:69` | Enabled |
| 301 — llm-gpu | pve-d1 | `enp6s18` / VirtIO | `vmbr0` | `10.44.0.170/24` via DHCP | `BC:24:11:3A:9E:55` | Enabled |

No VLAN tag is specified on these four guest NICs. DHCP reservations and address stability are tracked in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|networking questions]]. Guest allocations and services are in [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]].

## Other interfaces

- `pve-7450`: `wlp2s0` exists, is down, and has no IP address. A manual `nic1` configuration entry has no corresponding live interface; see [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|networking questions]].
- All five management bridges have IPv6 link-local addresses. No global IPv6 address was present on those bridges at verification.

## Firewall

`pve-firewall status` reports `Status: disabled/running` on all five hosts. The guest NIC firewall flags above are enabled on 101, 201, and 301, but do not establish an active Proxmox filtering policy. Other firewall layers and external access boundaries are tracked in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|Open Questions]].

## Access

VM 301 also has a `tailscale0` address of `100.78.156.52/32`.

My saved SSH aliases use `root` on port 22 for all five nodes, with key authentication. Proxmox administration uses each node's management address on HTTPS port 8006. Detailed access permissions and service endpoints are linked from [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]].
