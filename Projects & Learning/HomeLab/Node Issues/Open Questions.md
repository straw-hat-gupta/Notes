# Node Issues — Open Questions

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]]

| Question | Evidence needed |
| --- | --- |
| Which undated storage report corresponds to the retained June 20 abrupt ending or the long gap after the August 23 reboot? | Incident/recovery recollection, console state, and any additional retained evidence |
| Did E7450 reboot automatically during the update, lose its network link, or only lose cluster membership? | Update task timestamps, package logs, boot ID/uptime and journal boots, NIC/link history, Corosync logs |
| What is E7450's current reachability, when did the disconnect occur, and how long did it last? | Incident timing and host/cluster observations |
| What restores each node, and do they recover without intervention? | Recovery steps and timing |
| Does guest networking fail when the host disappears from Proxmox? | VM/LXC reachability during an incident |
| What triggers D1's transmit stall: physical adapter, driver, firmware, or another interaction? Has it recurred on the upgraded kernel? | A separately approved one-variable isolation test if needed; comparable uptime/workload evidence |
| What caused D1's older June 25 memory-pressure/FUSE/task stall? | Incident-specific host/management evidence; it is separate from the August/September NIC signature |
| What caused storage's June 20 abrupt journal ending? | Clock-aware peer correlation; console/crash/firmware evidence if available |
| Have the dropouts stopped recurring? | Sustained observations after a confirmed fix |

Completed historical assessment: [[Projects & Learning/HomeLab/Node Issues/D1 and Storage Evidence|D1 and Storage Evidence]]. The NIC transmit-path mechanism is strongly supported for three D1 events; storage's reported fault is not yet explained. No repair has been applied or validated.

Current state: [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]]. Replacement NIC details: [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Replacement NICs|Replacement NICs]]; neither card is installed.
