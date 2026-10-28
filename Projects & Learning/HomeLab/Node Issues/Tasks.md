# Node Issues — Tasks

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]] · [[Projects & Learning/Big Tasks|Big Tasks]]

- [x] Purchase two replacement NICs; confirm both remain uninstalled (2026-10-28).
- [x] Reconstruct retained D1/storage incident windows and recovery evidence; document unmapped reports and retention gaps in [[Projects & Learning/HomeLab/Node Issues/D1 and Storage Evidence|D1 and Storage Evidence]].
- [x] Collect and compare target logs, D2/E6420 witnesses, and retained Prometheus history for D1/storage only (2026-10-28).
- [ ] Establish the E7450 update timeline, current reachability, reboot/boot-ID evidence, and whether host, link, or only cluster membership was lost.
- [ ] Collect and compare BIOS/firmware event logs where available, kernel/system logs, NIC/link counters, and Corosync status for pve-d1, pve-storage, and pve-7450 around their respective incidents.
- [x] Assess retained NIC/link evidence: three D1 transmit-stall episodes are corroborated; storage has no equivalent retained NIC signature.
- [ ] Isolate D1's hardware/driver/firmware trigger only after accounting for the kernel update and protecting Career Ops; do not assume both nodes need a NIC swap.
- [ ] Identify the reported storage incident and resolve the June 20 / post-August-reboot evidence gaps.
- [ ] Determine the cause of D1's separate June 25 pressure/FUSE/task-stall episode if it remains operationally relevant.
- [ ] Choose a fix based on the evidence; evaluate the purchased NICs if replacement is warranted.
- [ ] Validate stable cluster membership and affected workloads after the fix.
