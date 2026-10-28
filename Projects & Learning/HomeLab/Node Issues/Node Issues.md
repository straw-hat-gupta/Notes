# Node Issues

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Outcome

Diagnose and fix pve-d1 and pve-storage dropping out of the Proxmox cluster while the physical machines remain powered on.

## Observed symptoms — reported 2026-10-27

- Both nodes have, while running, become unavailable and appeared offline in the Proxmox web interface.
- The physical computers downstairs remain on when this happens.
- Frequency, timestamps, recovery method, and whether both fail together are not known yet.
- pve-d1 hosts llm-gpu and [[Projects & Learning/Projects/Career Ops/Career Ops|Career Ops]]; impact on the VM during an outage still needs checking.

## Hypothesis and available hardware

The existing NICs may be involved. This is a hypothesis, not a diagnosis. Two replacement network interface cards have already been purchased; card models, compatibility, and installation state remain unknown.

## Investigation direction

Collect host/kernel, network, and cluster evidence around a dropout and distinguish a network-link failure, host problem, or cluster-membership problem before choosing a fix. Track evidence separately for each node.

## Connections

[[Projects & Learning/HomeLab/Agent Access/Agent Access|Agent Access]] should make remote investigation convenient. [[Projects & Learning/HomeLab/Homelab Setup/Node Inventory|Node Inventory]] supplies hardware context. Findings inform [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote Development]] placement.

## Tasks

![[Projects & Learning/HomeLab/Node Issues/Tasks]]
