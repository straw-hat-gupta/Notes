# Shared MCP Servers

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Outcome

Explore running MCP servers on the cluster so multiple agents can use a common set of tools, including a possible homelab-management server.

## Requirements captured

- Host reusable MCP tools on the cluster, reachable by the intended agents.
- Explore tools for homelab inspection and management.
- Agents may have different skills and permissions even when sharing a server.
- Keep agent instructions/skills distinct from the MCP servers that expose tools.

## Decisions still open

Which servers/tools are needed, where they run, supported client/transport options, authentication, network access, and permissions. No particular server or transport has been selected.

## Connections

[[Projects & Learning/HomeLab/Agent Access/Agent Access|Agent Access]] is a first consumer; [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote Development]] hosts other agent sessions; [[Projects & Learning/Learning/Agents and MCP/Agents and MCP|Agents and MCP]] supports the design.

## Tasks

![[Projects & Learning/HomeLab/Shared MCP Servers/Tasks]]
