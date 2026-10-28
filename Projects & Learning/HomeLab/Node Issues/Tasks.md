# Node Issues — Tasks

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]] · [[Projects & Learning/Big Tasks|Big Tasks]]

- [x] Purchase two replacement NICs; confirm both remain uninstalled (2026-10-28).
- [ ] Capture D1/storage dropout timestamps, frequency, whether failures coincide, and how each node recovers.
- [ ] Establish the E7450 update timeline, current reachability, reboot/boot-ID evidence, and whether host, link, or only cluster membership was lost.
- [ ] Collect and compare BIOS/firmware event logs where available, kernel/system logs, NIC/link counters, and Corosync status for pve-d1, pve-storage, and pve-7450 around their respective incidents.
- [ ] Check NIC/link behavior and other evidence to confirm or rule out the NIC hypothesis.
- [ ] Choose a fix based on the evidence; evaluate the purchased NICs if replacement is warranted.
- [ ] Validate stable cluster membership and affected workloads after the fix.
