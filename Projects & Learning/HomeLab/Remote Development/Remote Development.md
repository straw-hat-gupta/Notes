# Remote Development

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Outcome

Move development off the Mac into a homelab VM so repositories, tools, and long-running agents can stay there. Keep the Mac as a way to connect to the workspace.

## Requirements captured

- A dedicated place for all development work, with access from the Mac and eventually other devices.
- Agents and development processes can continue running remotely.
- Centralize [[Projects & Learning/Projects/Client Management/Client Management|Client Management]] first, including its notes, code, and environment.
- GPU access was mentioned as a possible development convenience. It is not a prerequisite for the development VM or connected agents.
- llm-gpu is a candidate, or a separate VM could be created. No VM/host choice or GPU-sharing arrangement has been decided.
- Existing llm-gpu on pve-d1 already has GPU access and runs [[Projects & Learning/Projects/Career Ops/Career Ops|Career Ops]].

## Decisions to make

VM placement, resources, OS, repository locations, remote access, editor workflow, and persistent agent sessions. Clarify what was meant by “Reverb Node” before treating it as a hostname or product.

## Connections

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]] informs host reliability; [[Projects & Learning/HomeLab/Node Inventory|Node Inventory]] informs capacity. Earlier requirements carried forward: an always-on programming environment, a clean laptop, and convenient access from any device. A Cloudflare tunnel was floated as one option, not selected.

## Tasks

![[Projects & Learning/HomeLab/Remote Development/Tasks]]
