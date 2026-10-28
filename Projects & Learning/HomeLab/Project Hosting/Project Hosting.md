# Project Hosting

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Goal

I want projects, demos, and personal tools hosted on the homelab, with subdomains routed to the appropriate services.

## Current context

LXC 101 cf-tunnel runs cloudflared on pve-d2. LXC 100 app-runner runs the AI dashboard. Runtime details are in [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]].

The domain was recorded as `smarthg.dev`. Its exact spelling, DNS, public tunnel routes, and access policies are tracked in [[Projects & Learning/HomeLab/Project Hosting/Open Questions|Open Questions]].

My Cloudflare setup is still minimal ([[Projects & Learning/HomeLab/ANSWERS|ANSWERS]], 2026-10-27); the running tunnel alone does not establish the public routes.

## Requirements

- Host the portfolio on the homelab and make it reachable through the domain.
- Give selected demos public access and personal services the intended remote restrictions.
- Route distinct application hostnames to their VM/container/service.

## Service portability and recovery

I want Career Ops reconfigured from its current llm-gpu setup into Docker or an equivalent portable deployment, reachable remotely. If the hosting node goes down, the service should recover on another node. This should be the general pattern for services, tools, and projects hosted on the cluster. Confirmed in [[Projects & Learning/HomeLab/ANSWERS|ANSWERS]], 2026-10-27.

Container packaging alone does not provide failover. Proxmox HA can recover guests after a node failure, but it restarts them elsewhere rather than moving the failed host's live process state. Recovery needs reachable data, available capacity, compatible networking, and working quorum/fencing. The current GPU passthrough ties llm-gpu to D1's hardware, so a portable application host needs its GPU dependency decided separately. [Proxmox HA guide](https://github.com/proxmox/pve-docs/blob/master/ha-manager.adoc).

The proposed single TrueNAS node and striped data pool would remain shared failure points. Host failover cannot recover applications whose only data copy is on an unavailable storage node. The [[Projects & Learning/HomeLab/Homelab Setup/Storage/Storage Configuration#Planned TrueNAS setup|storage plan]] and failover design need to account for that dependency.

Architecture, persistent data, acceptable downtime, and access decisions are in [[Projects & Learning/HomeLab/Project Hosting/Open Questions|Open Questions]].

## Connections

[[Projects & Learning/Learning/Cloudflare/Cloudflare|Cloudflare]] · [[Projects & Learning/Projects/Portfolio/Portfolio|Portfolio]] · [[Projects & Learning/Projects/AIVA/AIVA|AIVA]] · [[Projects & Learning/Projects/App Study/App Study|App Study]]

## Tasks

![[Projects & Learning/HomeLab/Project Hosting/Tasks]]
