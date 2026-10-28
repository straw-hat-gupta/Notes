# Agent Access

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Outcome

Talk to an agent through the ChatGPT desktop app and have it use the necessary tools, skills, and MCP connections to inspect and help configure the homelab.

## Requirements captured

- Convenient conversational access to the homelab from the desktop app.
- Reach the relevant Proxmox nodes and collect logs for [[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]].
- Reusable knowledge/skills for homelab management and tools for the operations needed.
- Confirm what the chosen ChatGPT desktop workflow actually supports before selecting an integration. Do not assume that this chat's local SSH access is automatically available to another agent or app.

## Current access evidence

Earlier in this chat, direct SSH to pve-d2 as root succeeded; cluster membership listed all five nodes. From D2, SSH to pve-6420 succeeded. Checks to pve-d1, pve-7450, and pve-storage stopped at host-key verification, so those paths are not yet confirmed end-to-end. This is access evidence, not a report on current node health.

## Connections

[[Projects & Learning/HomeLab/Shared MCP Servers/Shared MCP Servers|Shared MCP Servers]] provides reusable tools; [[Projects & Learning/Learning/Agents and MCP/Agents and MCP|Agents and MCP]] tracks the concepts to learn. Existing source: [[HomeLab/TODO]].

## Tasks

![[Projects & Learning/HomeLab/Agent Access/Tasks]]
