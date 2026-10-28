# Node Issues — Open Questions

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]]

| Question | Evidence needed |
| --- | --- |
| When do the dropouts occur, how often, and do D1/storage fail together? | Incident timestamps and monitoring history |
| What restores each node, and do they recover without intervention? | Recovery steps and timing |
| Does guest networking fail when the host disappears from Proxmox? | VM/LXC reachability during an incident |
| Is the failure in the host, physical link, management network, or cluster membership? | BIOS/firmware events where available, kernel logs, NIC/link counters, and Corosync evidence |
| Have the dropouts stopped recurring? | Sustained observations after a confirmed fix |

Current state: [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]]. Replacement NIC details: [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Hardware|Hardware questions]].
