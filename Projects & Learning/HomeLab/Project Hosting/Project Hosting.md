# Project Hosting

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Goal

I want projects, demos, and personal tools hosted on the homelab, with subdomains routed to the appropriate services.

## Current context

LXC 101 cf-tunnel runs cloudflared on pve-d2. LXC 100 app-runner runs the AI dashboard. Runtime details are in [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]].

The domain was recorded as `smarthg.dev`. Its exact spelling, DNS, public tunnel routes, and access policies are tracked in [[Projects & Learning/HomeLab/Project Hosting/Open Questions|Open Questions]].

## Requirements

- Host the portfolio on the homelab and make it reachable through the domain.
- Give selected demos public access and personal services the intended remote restrictions.
- Route distinct application hostnames to their VM/container/service.

## Connections

[[Projects & Learning/Learning/Cloudflare/Cloudflare|Cloudflare]] · [[Projects & Learning/Projects/Portfolio/Portfolio|Portfolio]] · [[Projects & Learning/Projects/AIVA/AIVA|AIVA]] · [[Projects & Learning/Projects/App Study/App Study|App Study]]

## Tasks

![[Projects & Learning/HomeLab/Project Hosting/Tasks]]
