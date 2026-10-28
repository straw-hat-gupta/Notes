# Access

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|Access questions]]

Verified 2026-10-27 from the local Codex environment using saved SSH aliases, key authentication, and existing known-host verification.

## SSH connections

| Alias | Host | SSH user | Port | Verified access |
| --- | --- | --- | --- | --- |
| pve-d1 | 10.44.0.50 | root | 22 | Root shell; Proxmox configuration readable |
| pve-d2 | 10.44.0.51 | root | 22 | Root shell; Proxmox configuration readable |
| pve-6420 | 10.44.0.52 | root | 22 | Root shell; Proxmox configuration readable |
| pve-7450 | 10.44.0.53 | root | 22 | Root shell; Proxmox configuration readable |
| pve-storage | 10.44.0.54 | root | 22 | Root shell; Proxmox configuration readable |

## Administrative scope

My saved host connections provide broad root permissions: hardware and health inspection, system/configuration files, Proxmox commands, storage metadata, networking, and VM/container administration. They are not restricted to read-only commands.

LXC 100, 101, and 201 can be inspected through their hosts with `pct exec`. VM 301's QEMU guest agent responds to OS/network queries and guest commands. Separate guest SSH authentication was not tested during this inventory.

The inventory used diagnostic commands only. Infrastructure changes remain subject to [[Projects & Learning/HomeLab/AGENTS|the HomeLab change boundaries]]. Private keys, tokens, passwords, and secret-bearing service configuration stay outside this vault.

## Management paths

- Proxmox web/API: each management address on HTTPS port 8006.
- Host SSH: the aliases above on port 22.
- Guest network paths: [[Projects & Learning/HomeLab/Homelab Setup/Network/Network Configuration#Guest connections|Guest connections]].
- Current application endpoints: [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services#Services|Services]].
- ChatGPT/MCP integration work: [[Projects & Learning/HomeLab/Agent Access/Agent Access|Agent Access]]. These local SSH connections do not establish access from another client or execution host.

Source: `ssh -G`, successful `ssh` sessions with `id` reporting UID 0, `pvesh`, `pct exec`, and QEMU guest-agent queries. [[Projects & Learning/HomeLab/Homelab Setup/Evidence/2026-10-27.json|Evidence snapshot]].
