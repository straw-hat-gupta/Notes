# Node Issues

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Goal

Find the causes of D1/storage cluster dropouts and the E7450 disconnect during an update, then validate the appropriate fixes.

## Reported behavior — 2026-10-27

- pve-d1 and pve-storage have become unavailable and appeared offline in Proxmox while still powered on.
- D1 hosts llm-gpu and [[Projects & Learning/Projects/Career Ops/Career Ops|Career Ops]].
- Two replacement NICs have been purchased and neither is installed (confirmed 2026-10-28). They are reserved for D1/storage only if diagnosis supports NIC replacement. Details: [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory#Replacement NICs|Replacement NICs]].

The NICs are a possible cause, not a confirmed diagnosis.

## E7450 update-time disconnect — reported 2026-10-28

While updating pve-7450 through the Proxmox web Updates tab, it disconnected from the cluster. I did not initiate a reboot. An automatic reboot, loss of network reachability, host failure, or a Corosync-only disconnect has not yet been established. Exact incident time, duration, current reachability, and recovery behavior are still to collect.

I updated all five nodes; installed package and running-kernel versions are not yet rechecked. Source: [[Projects & Learning/HomeLab/Homelab Setup/Answers|Answers]].

## Last live observation

D1 and storage were reachable over SSH and present in the quorate cluster on 2026-10-27 at 21:37 MDT. No fix was applied during the inventory. Current readings and faults are in [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]].

This predates the reported all-node updates and the E7450 incident. Incident timing, recovery behavior, and root-cause questions are in [[Projects & Learning/HomeLab/Node Issues/Open Questions|Open Questions]].

## Investigation

Correlate host/kernel, network, and cluster evidence around a dropout before choosing a fix. Keep D1, storage, and E7450 evidence separate. Similar disconnect symptoms do not establish the same cause. The next diagnosis plan will also account for the [[Projects & Learning/HomeLab/Homelab Setup/Status|GPU, OpenIPMI, and disk-health records]].

## Connections

[[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory|Hardware]] · [[Projects & Learning/HomeLab/Agent Access/Agent Access|Agent Access]] · [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote Development]]

## Tasks

![[Projects & Learning/HomeLab/Node Issues/Tasks]]
