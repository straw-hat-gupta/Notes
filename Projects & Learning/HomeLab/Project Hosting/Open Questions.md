# Project Hosting — Open Questions

[[Projects & Learning/HomeLab/Project Hosting/Project Hosting|Project Hosting]]

| Question | Context |
| --- | --- |
| Is `smarthg.dev` the exact registered domain spelling? | Existing notes contain this spelling. |
| Which DNS records, Cloudflare tunnel routes, and origins are currently configured? | cloudflared is active in LXC 101; public routes were not inspected. |
| Which services should be public, private, or authenticated? | Each application needs an explicit access choice. |
| Where should new services run, and how should deployment work? | Coolify was mentioned for prototypes but is not selected. |
| How should portfolio/demo subdomains map to services? | Routing choices remain open. |
