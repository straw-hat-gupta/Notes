# HomeLab agent instructions

These instructions apply to this directory and all descendants. Follow [[Projects & Learning/AGENTS|the Projects & Learning agent guide]] as well.

## Inventory and setup records

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] is the home for the homelab's current hardware, configuration, and operational status. Keep the setup documents in that folder as the source of truth. This includes:

- Nodes, CPUs, GPUs, NICs, and other installed hardware.
- Installed RAM, module sizes and slot layout when known, and VM/container memory allocations.
- Physical disks, boot devices, pools, RAID/ZFS layout, filesystems, datasets, mounts, storage sharing, and workload storage assignments.
- Network topology, interfaces, bridges, VLANs, addresses, and access configuration.
- Proxmox and other relevant software configuration, VM/container placement, services, and workloads.
- Current node/service health, known faults, and confirmed resolutions.

Use [[Projects & Learning/HomeLab/Homelab Setup/Node Inventory|Node Inventory]] for the existing node and workload record. Add focused setup notes within Homelab Setup when there is enough confirmed detail to warrant them, and link them from its overview. Keep one authoritative record for each fact and link to it from other notes.

## Required with every edit

Whenever you edit any HomeLab note, review whether the edit changes or reveals a fact about the actual setup. Whenever the user confirms a setup change, or authorized work produces evidence of a change, update the affected inventory/setup documents as part of the same work. This applies to additions, removals, replacements, configuration changes, workload moves, faults, and recoveries.

1. Read the relevant inventory/setup notes before editing.
2. Update the current-state records with every affected confirmed fact. Record the date and source of confirmation, such as a user report or diagnostic result, when available.
3. Reconcile related overviews and Tasks notes so they agree. Keep actionable checklists in their existing Tasks.md files.
4. Before saving, check that the setup records reflect the confirmed result. Briefly report which records changed and any remaining uncertainty.

A wording-only edit or a proposed plan may require no inventory change; still make the review. Do not rewrite unchanged inventory or claim it was freshly verified. Plans, intended configurations, guesses, and unchecked tasks are not evidence that the setup changed. Clearly label unknown, historical, conflicting, and unverified details. Do not invent missing RAM, storage, network, or status information.

Record the current state in the setup documents even when supporting diagnostics or history live in another outcome folder. Link to that evidence instead of leaving the only record of a confirmed change buried in a task or conversation.

## Boundaries

Never store passwords, tokens, private keys, or other secrets here. Maintaining these records does not authorize live infrastructure changes. Follow the user's authorized scope and the parent guide's approval requirements.
