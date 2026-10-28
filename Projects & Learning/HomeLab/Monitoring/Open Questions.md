# Monitoring — Open Questions

[[Projects & Learning/HomeLab/Monitoring/Monitoring|Monitoring]]

| Question | Context |
| --- | --- |
| Which parts of the current stack should be retained, reconfigured, or replaced? | A useful per-node and whole-homelab dashboard is the goal; a replacement is not selected. |
| Which dashboard panels and aggregates are needed? | Include per-node load/stats and cluster totals for RAM, CPU/cores, and storage usage. Existing definitions were not collected. |
| What retention and alert notification routes are configured? | Service/data locations are recorded; secret-bearing configuration contents were excluded. |
| Which benchmark controls and history are worth adding? | Button-triggered and scheduled benchmarks remain ideas. |
| How should GPU metrics be collected once the VM's NVIDIA driver issue is resolved? | The current driver query fails. |
