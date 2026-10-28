# Shared MCP Servers — Open Questions

[[Projects & Learning/HomeLab/Shared MCP Servers/Shared MCP Servers|Shared MCP Servers]]

| Question | Context |
| --- | --- |
| Which MCP servers and operations are useful? | Include homelab management and request-to-LXC/container service provisioning. |
| What information should a service request provide, and when should Docker run inside the LXC? | This workflow is desired; runtime selection and automation design remain undecided. |
| Which VM/container should host them? | Placement is not selected. |
| Which clients and transports need support? | Multiple agents should be able to share the tools. |
| How should authentication, network access, and permissions work? | Shared tools do not imply identical permissions for every agent. |
