# Node Issues — Open Questions

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]]

| Question | Evidence needed |
| --- | --- |
| When do the dropouts occur, how often, and do D1/storage fail together? | Incident timestamps and monitoring history |
| Did E7450 reboot automatically during the update, lose its network link, or only lose cluster membership? | Update task timestamps, package logs, boot ID/uptime and journal boots, NIC/link history, Corosync logs |
| What is E7450's current reachability, when did the disconnect occur, and how long did it last? | Incident timing and host/cluster observations |
| What restores each node, and do they recover without intervention? | Recovery steps and timing |
| Does guest networking fail when the host disappears from Proxmox? | VM/LXC reachability during an incident |
| Is the failure in the host, physical link, management network, or cluster membership? | BIOS/firmware events where available, kernel logs, NIC/link counters, and Corosync evidence |
| Have the dropouts stopped recurring? | Sustained observations after a confirmed fix |

Current state: [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]]. Replacement NIC details: [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Replacement NICs|Replacement NICs]]; neither card is installed.
