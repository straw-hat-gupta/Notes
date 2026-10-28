# Project Hosting — Open Questions

[[Projects & Learning/HomeLab/Project Hosting/Project Hosting|Project Hosting]]

| Question | Context |
| --- | --- |
| Is `smarthg.dev` the exact registered domain spelling? | Existing notes contain this spelling. |
| Which DNS records, Cloudflare tunnel routes, and origins are currently configured? | cloudflared is active in LXC 101; public routes were not inspected. |
| Which services should be public, private, or authenticated? | Each application needs an explicit access choice. |
| Where should new services run, and how should deployment work? | Coolify was mentioned for prototypes but is not selected. |
| How should portfolio/demo subdomains map to services? | Routing choices remain open; Cloudflare setup is still minimal. |
| Which layer should manage service failover, and what downtime/data loss is acceptable? | Docker or an equivalent package is desired; orchestration/HA is not selected. |
| Where will persistent state remain available after a compute or storage-node failure? | A single TrueNAS node with a striped pool would not provide storage failover. |
| Does Career Ops require the GPU, and what are its exact processes, dependencies, paths, and restore steps? | The entire service is in scope for backup and a dedicated LXC/container; the implementation inventory is still needed. |
