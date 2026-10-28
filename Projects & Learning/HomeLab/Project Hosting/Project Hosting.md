# Project Hosting

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Outcome

Use the homelab and a Cloudflare-managed domain to host projects, demos, and personal tools, with different subdomains pointing to the appropriate services.

## Requirements captured

- Domain reported as `SmirthG.dev`; confirm the exact registered spelling first.
- Cloudflare is already involved, but current DNS and other configuration have not been inspected.
- The portfolio should run on the homelab and be reachable through the domain.
- Selected demos should be accessible to other people; personal services should be accessible remotely with the intended access restrictions.
- Different applications need distinct addresses and routing to the right VM/container/service.

## Decisions still open

Where services run, how deployment works, how traffic reaches the cluster, how subdomains are routed, and which services are public versus private. Compare appropriate routing/access approaches before choosing one. Existing Client Management notes mention Coolify as a candidate for prototypes; it is not selected yet.

## Connections

[[Projects & Learning/Learning/Cloudflare/Cloudflare|Learn Cloudflare]] supports this task. Consumers include [[Projects & Learning/Projects/Portfolio/Portfolio|Portfolio]], [[Projects & Learning/Projects/AIVA/AIVA|AIVA]], and a possible personal [[Projects & Learning/Projects/App Study/App Study|App Study]] application.

## Tasks

![[Projects & Learning/HomeLab/Project Hosting/Tasks]]
