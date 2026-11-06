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

## Physical connections

All five Proxmox nodes use static IPs and connect by individual Ethernet cables to a TP-Link 8-port switch. Confirmed 2026-10-27. Exact switch/router models, port mapping, and DHCP reservations remain in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|Networking questions]].

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

- `pve-7450`: `wlp2s0` exists, is down, and has no IP address. The manual `nic1` entry is a mistake; I want to remove it after checking dependencies (confirmed 2026-10-28). It remains present in the last collected configuration; dependency checks and the configuration change are pending in [[Projects & Learning/HomeLab/Homelab Setup/Tasks|Tasks]].
- All five management bridges have IPv6 link-local addresses. No global IPv6 address was present on those bridges at verification.

## D1/storage scoped check — 2026-10-28

D1 and storage retained the recorded nic0/vmbr0 address/bridge layout at the read-only 10:42 MDT check. Both nic0 links negotiated 1 Gb/s full duplex. The `rx_errors`, `tx_errors`, and `tx_timeout_count` counters were zero after the latest boots; EEE was enabled but inactive. These current settings/counters neither disprove historical stalls nor identify their trigger. [[Projects & Learning/HomeLab/Node Issues/D1 and Storage Evidence|D1 and Storage Evidence]] contains the timeline and causal limits.

## Firewall

`pve-firewall status` reports `Status: disabled/running` on all five hosts. The guest NIC firewall flags above are enabled on 101, 201, and 301, but do not establish an active Proxmox filtering policy. I have not intentionally configured firewall rules or custom Tailscale access settings (confirmed 2026-10-27). Effective router/account defaults and the intended access boundaries remain in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|Open Questions]].

## Access

Tailscale is installed on pve-d2 and llm-gpu (confirmed 2026-10-27). VM 301 has an observed `tailscale0` address of `100.78.156.52/32`. Pve-d2 Tailscale runtime details were not included in the live snapshot.

My saved SSH aliases use `root` on port 22 for all five nodes, with key authentication. Proxmox administration uses each node's management address on HTTPS port 8006. Detailed access permissions and service endpoints are linked from [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]].

## Home Wi-Fi access point setup (2026-11-06)

- Main gateway: Technicolor CGM4141, `10.44.0.1/24`; DHCP pool `10.44.0.2`–`10.44.0.253` (2-day lease).
- Main Wi-Fi: SSID `Sam` on both 2.4 GHz and 5 GHz; WPA2-PSK (AES). Automatic channels observed as 6 (2.4 GHz) and 44 (5 GHz).
- Planned basement wired AP: D-Link DIR-882, **hardware revision A1**, **F/W Ver. 1.01 printed on bottom label** (factory-label version, currently installed version not yet verified). User confirms factory reset completed.
- Existing unmanaged basement switch remains connected to homelab. D-Link must stay isolated until DHCP is disabled or genuine AP mode configured.
- Candidate D-Link management IP `10.44.0.254/24` remains unverified for conflicts and is **not configured**.

- 2026-11-06 DIR-882 A1 setup progress: user connected directly to factory-reset device at `http://192.168.0.1` and sees the **initial setup wizard**. No configuration changes reported. Next: inspect first wizard screen before choosing any options.

- 2026-11-06 DIR-882 A1 wizard screenshot: admin header shows **Firmware Version 1.04 currently installed**, whereas bottom sticker says 1.01. Initial Install wizard requests connecting the INTERNET/WAN port to a broadband modem and power cycling modem. **Do not follow this router-mode wizard** for the intended wired AP configuration. Next action: close wizard with top-right X, keeping D-Link isolated from basement switch.

- 2026-11-06 DIR-882 A1 firmware 1.04: initial setup wizard successfully closed; Home dashboard visible. Dashboard reports Internet Disconnected, WAN cable disconnected, WAN connection type Dynamic IP (DHCP), no WAN IP/gateway/DNS, 1 connected client. WAN MAC displayed `28:3B:82:64:B3:95`. This is expected while isolated for AP configuration. Next: inspect Settings menu without changing settings.

- 2026-11-06 DIR-882 A1 firmware 1.04 Settings dropdown screenshot: menu items **Wizard, Internet, Wireless, Network, USB Sharing**. No dedicated Access Point mode is visible in this menu (does not rule out elsewhere). Next: inspect **Settings > Network** page without saving changes.

- 2026-11-06 DIR-882 A1 firmware 1.04 **Settings > Network** screenshot, factory-default values: LAN `192.168.0.1`, mask `255.255.255.0`, management hostname `dlinkrouter.local`, local domain blank; DNS Relay enabled; DHCP server enabled, pool `192.168.0.100`–`192.168.0.199`, lease `10080` minutes, Always Broadcast disabled. Advanced: WAN port speed Auto, UPnP enabled, IPv4 multicast streams disabled, IPv6 multicast streams disabled. No changes applied. Next step: while D-Link remains disconnected from basement switch, disable its DHCP server and save; then reconnect directly if necessary. Planned management IP `10.44.0.254` still requires conflict check before assignment.

- 2026-11-06 DIR-882 A1 firmware 1.04: user **disabled DHCP Server under Settings > Network and clicked Save**, reporting save succeeded. This is user-confirmed; no post-save screenshot or independent verification yet. D-Link intended to remain isolated from basement switch. LAN IP remains `192.168.0.1` unless subsequently changed. Next: verify that candidate `10.44.0.254` is free before changing the AP management address.

- 2026-11-06 management-IP conflict check: user pinged proposed `10.44.0.254` from main `Sam` Wi-Fi and reported **timeout / no replies**. This does **not** prove the IP is unused; next check is ARP/neighbor cache and router device/reservation list before assignment. No D-Link LAN IP change yet.

- 2026-11-06 further IP check: after a ping timeout to proposed management IP `10.44.0.254`, user ran `arp -a` on a computer connected to main `Sam` Wi-Fi and reported **no entry for 10.44.0.254**. Address is still not conclusively proven unused; check Technicolor connected devices and reserved/static assignments before setting D-Link LAN IP. No D-Link LAN IP change yet.

- 2026-11-06 Technicolor Connected Devices check: user reports **10.44.0.254 not listed**. Together with ping timeout and absent ARP entry, no current conflict has been detected, but offline devices or undocumented static assignments cannot be conclusively ruled out. Technicolor DHCP range ends at .253, so .254 is outside its observed pool. No management IP assigned to D-Link yet. Next: configure isolated DIR-882 LAN IP as `10.44.0.254/24`, keeping its DHCP disabled; note that changing IP will disconnect the current admin session.

- 2026-11-06 DIR-882 A1 (installed firmware 1.04): user reports successfully saving **LAN IP `10.44.0.254`, subnet mask `255.255.255.0`, DHCP server disabled** in Settings > Network. User-confirmed save; management connectivity at new IP not yet independently verified. D-Link should remain disconnected from basement switch. Next: test management access at `10.44.0.254` using a laptop connected to the main `Sam` network only after a safe isolated connection plan, or directly with temporary static laptop address; avoid joining the live LAN until AP bridging is finalized.

- 2026-11-06 DIR-882 management connectivity verification: user selected **help** when instructed to configure a temporary static Ethernet IP on the laptop. They have **not yet confirmed** opening `http://10.44.0.254`. Next action: identify laptop operating system so exact static-IP instructions can be given one step at a time. D-Link remains isolated from basement switch.

- 2026-11-06 laptop OS confirmed **macOS** for DIR-882 isolated management test. Next: configure Mac Ethernet interface manually with IPv4 `10.44.0.250`, subnet `255.255.255.0`, router blank, while connected to a numbered DIR-882 LAN port; do not connect D-Link to basement switch. Management URL `http://10.44.0.254` still unverified.

- 2026-11-06 macOS Ethernet temporary static IP setup: user confirmed **saved successfully** with manual IPv4 `10.44.0.250/24` (`255.255.255.0`) and router/gateway left blank. Mac should remain directly connected to a numbered DIR-882 LAN port; D-Link remains isolated from basement switch. Next verify D-Link management UI at `http://10.44.0.254`.

- 2026-11-06 DIR-882 management verification: user successfully opened the **D-Link dashboard at `http://10.44.0.254`** from macOS laptop using direct LAN cable and temporary manual Ethernet IP `10.44.0.250/24` (no gateway). This confirms management connectivity at the new LAN IP while D-Link is isolated from the basement switch and DHCP is disabled. Next inspect D-Link Settings > Wireless to configure SSID/security to match main gateway; no uplink connection yet.

- 2026-11-06 DIR-882 Settings > Wireless screenshot inspection (credentials intentionally omitted): Smart Connect disabled. 2.4 GHz enabled, SSID `D-Link_DIR-882`, Security Mode **None** (currently open), mixed 802.11b/g/n, channel Auto, power High, width Auto 20/40 MHz, HT20/40 coexistence enabled, visible, always enabled. 5 GHz enabled, SSID `dlink-B392`, Security Mode WPA/WPA2-Personal, mixed 802.11a/n/ac, channel Auto, power High, width Auto 20/40/80 MHz, visible, always enabled. WPS-PBC and WPS-PIN disabled. Screenshot displayed a 5 GHz Wi-Fi password; **do not store or reproduce it**. Main gateway SSID `Sam` on both bands with WPA2-PSK AES. Next inspect available 2.4 GHz Security Mode dropdown options, without changing or saving settings, before choosing WPA2-only compatibility.

- 2026-11-06 DIR-882 2.4 GHz Security Mode dropdown: user reports **WPA/WPA2-Personal is the only available secured option** (in addition to current None). Next select WPA/WPA2-Personal for 2.4 GHz, without saving or changing other fields yet. No Wi-Fi credentials recorded.

- DIR-882 wireless setup progress: 2.4 GHz SSID changed from `D-Link_DIR-882` to `Sam`. WPA/WPA2-Personal selected. Changes are not yet saved to the router. No Wi-Fi passwords recorded.

- 2026-11-06 DIR-882 wireless setup: user changed 5 GHz SSID from `dlink-B392` to `Sam`, matching the primary Technicolor SSID. This change is **not yet saved** to the router. The 2.4 GHz SSID was also set to `Sam` and WPA/WPA2-Personal selected without saving. Next configure Wi-Fi passwords locally, without sharing or recording credentials.

- 2026-11-06 DIR-882 wireless configuration: 2.4 GHz credential was entered locally but changes remain unsaved. User reported an issue when attempting to enter the 5 GHz credential. Exact issue not yet known. No credential values are recorded. Next ask user what happens in the 5 GHz field before making any other changes.

- 2026-11-06 DIR-882 wireless setup: user reports the 5 GHz Wi-Fi password field is **disabled/greyed out and cannot be edited**. Wireless changes remain unsaved. No credentials recorded. Next inspect whether Smart Connect or another setting is controlling the field, using a redacted screenshot before further edits.

- 2026-11-06 DIR-882 wireless setup: user suspects the **5 GHz radio is currently disabled**, which may explain why the 5 GHz password field is greyed out. This is user observation, not yet independently verified. Next enable 5 GHz Status on Settings > Wireless without saving, then check whether password field becomes editable. No passwords recorded.
