# Node Issues

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Goal

Find and fix the cause of D1 and storage dropping out of the cluster while their computers remain powered on.

## Reported behavior — 2026-10-27

- pve-d1 and pve-storage have become unavailable and appeared offline in Proxmox while still powered on.
- D1 hosts llm-gpu and [[Projects & Learning/Projects/Career Ops/Career Ops|Career Ops]].
- Two replacement NICs have been purchased. Their details are in [[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Hardware|Hardware questions]].

The NICs are a possible cause, not a confirmed diagnosis.

## Latest observation

Both hosts were reachable over SSH and present in the quorate cluster on 2026-10-27 at 21:37 MDT. No fix was applied during the inventory. Current readings and faults are in [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]].

Incident timing, recovery behavior, and root-cause questions are in [[Projects & Learning/HomeLab/Node Issues/Open Questions|Open Questions]].

## Investigation

Correlate host/kernel, network, and cluster evidence around a dropout before choosing a fix. Keep D1 and storage evidence separate so a shared symptom does not become an assumed shared cause.

## Connections

[[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory|Hardware]] · [[Projects & Learning/HomeLab/Agent Access/Agent Access|Agent Access]] · [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote Development]]

## Tasks

![[Projects & Learning/HomeLab/Node Issues/Tasks]]
