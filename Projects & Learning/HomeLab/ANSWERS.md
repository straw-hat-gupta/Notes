
H1 : [StarTech ST1000SPEXI](https://retail.era.ca/collections/networking-components/products/startech-com-st1000spexi-1-port-gigabit-ethernet-pcie-network-adapter-card)**9/10****$17.50**, used and described as tested. One in stock when checked. Intel I210 controller, one 1 Gbps RJ45 port, PCIe x1. [retail.era](https://retail.era.ca/collections/networking-components/products/startech-com-st1000spexi-1-port-gigabit-ethernet-pcie-network-adapter-card?_fid=e2fac8055&_pos=33&_ss=c&utm_source=chatgpt.com)**2**[Intel Gigabit CT, EXPI9301CTBLK](https://retail.era.ca/collections/networking-components/products/intel-gigabit-ct-desktop-adapter-expi9301ctblk-pcie-x1-nic?utm_source=chatgpt.com)**8.5/10****$17.50**, used and described as tested. One in stock when checked. This is the same model as your earlier photo: Intel 82574L, one 1 Gbps RJ45 port, PCIe x1. [retail.era](https://retail.era.ca/collections/networking-components/products/intel-gigabit-ct-desktop-adapter-expi9301ctblk-pcie-x1-nic?utm_source=chatgpt.com)
H2: what it says in SMBIOS
H3: 8gbb vram its a 1070 asus rog strix

s1: no backups have been established
s2: pve-storage will have true nas running on it and the two HDDs will be zfs stripped not mirrored so i get the full 2tb from them. the extra ssd idk what would be the best use of it maybe for installing true nas suggest what woudl be the best use of it. pve-storage is also where the backups, linux iso, and any data that needs to be shared by the other nodes will live here. maybe a network drive setup as well if its feasable. 
s3: none

N1: all the nodes have static ips. they all connected via a tp-link 8 port switch with a ethernet per node. 
N2: idk. might have been a mistake
N3: i have not set anything up. i have tailscale installed on pve-d2 and llm-gpu. but nothing other than that. 
N4: not much is setup in cloudflare right now

C1: yah gotta update all of them. they should be aligned. 
C2: i need to reconfigure career-ops properly. currently it runs in llm-gpu. and i access it by acessing llm-gpu. in the future i want to be able to run it in a docker container or something such that i can access it from anywhere and if the node its running goes down it auto migrates. i want this kind of setup for any service or tool or project i host on my cluster
C3: i want maybe change my stack/reconfigure properly for this. basicaly the goal will be a dashbaord that shows the loads on each node, different stats per-node and on a homelab level like ram, core/cpu, storage usage.

T1: idk needs to be diagnosed and fixed.
T2: idk and idk what IPMI is.
T3: idk this needs to diagnosed and fixed as well by looking at the bios logs and whatever else is needed.
T4: idk gotta figure it out