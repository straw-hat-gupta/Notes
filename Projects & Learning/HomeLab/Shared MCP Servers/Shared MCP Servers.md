# Shared MCP Servers

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Goal

I want to explore cluster-hosted MCP servers so multiple agents can use common tools, including homelab inspection and management.

## Future service-provisioning workflow

I want to request a service through the eventual MCP/plugin tools and have the workflow provision a suitable LXC/container, optionally running Docker inside an LXC. Career Ops is the first concrete migration target. The workflow should fit the cluster's storage, access, backup, and service-recovery setup. Confirmed 2026-10-28.

This is a future capability. The immediate next step is diagnosis planning for the current issues, followed by the required basic homelab configuration. Runtime choices and the provisioning interface are still open.

## Requirements

- Shared tools reachable by the intended clients.
- Separate agent skills/instructions from the servers that expose operations.
- Permissions appropriate to each agent and operation.

Server selection, placement, transport, authentication, and client access are in [[Projects & Learning/HomeLab/Shared MCP Servers/Open Questions|Open Questions]].

## Connections

[[Projects & Learning/HomeLab/Agent Access/Agent Access|Agent Access]] · [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote Development]] · [[Projects & Learning/Learning/Agents and MCP/Agents and MCP|Agents and MCP]]

## Tasks

![[Projects & Learning/HomeLab/Shared MCP Servers/Tasks]]
