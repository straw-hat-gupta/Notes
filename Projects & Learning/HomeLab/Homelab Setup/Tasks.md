# Homelab Setup — Tasks

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Open Questions|Open Questions]]

## Recorded

- [x] Verify hardware against all five live nodes, including pve-d1 GPU and SSD details.
- [x] Record current VM/container placement and each workload's purpose; keep unverified application details in Open Questions.
- [x] Record the installed storage layout and network hardware.
- [x] Identify the purchased replacement NIC models and record D1's ASUS ROG Strix GTX 1070 with 8 GB VRAM.
- [x] Confirm backup/share status: no backups established and no existing external storage shares/clients.
- [x] Record the TrueNAS storage plan and the host-version alignment decision (confirmed 2026-10-27).
- [x] Confirm that neither replacement NIC is installed; reserve them for D1/storage only if NIC faults are established (2026-10-28).
- [x] Confirm no data needing backup/preservation on the two storage HDDs or spare SSD (2026-10-28).
- [x] Update all five nodes (reported complete 2026-10-28; installed/running-version verification remains pending).

## Diagnosis progress

- [x] Complete the historical read-only D1/storage investigation and [[Projects & Learning/HomeLab/Node Issues/D1 and Storage Evidence|D1 and Storage Evidence]]; correlate three D1 transmit-stall episodes and retain storage/older-host-stall uncertainties.
- [x] Verify D1/storage PVE and running-kernel versions after their reported updates; both run the same checked baseline. Other nodes remain outside this verification.

## Remaining diagnosis planning

- [ ] Prepare the diagnosis plan for D1/storage dropouts, the E7450 update-time disconnect, the VM GPU driver failure, OpenIPMI/metric coverage, and SMART interpretation. Include evidence to collect, how to distinguish causes, Career Ops protection, and validation before any proposed repair.

## Storage and protection

- [ ] Inventory and back up all Career Ops installation/configuration/state on llm-gpu; define the destination, schedule, retention, independent/offsite copy, and restore test ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|S1]]).
- [ ] Compare TrueNAS VM and bare-metal tradeoffs for this hardware, explain the options, and choose disk access and the spare SSD's role ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|S4]]).
- [ ] Prepare the TrueNAS/striped-pool/share configuration and rollback plan for review before installation.
- [ ] Explain datasets/share protocols and propose the simplest client/permission setup for backups, Linux ISOs, shared data, and the network drive ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|S5]]).

## Hosts and faults

- [ ] Verify installed Proxmox/package versions, running kernels, reboot requirements, and cluster membership after the reported updates; recommend a consistent maintenance approach ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Configuration|C1]]).
- [ ] Diagnose llm-gpu's NVIDIA driver failure and prepare the smallest repair ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status|T1]]).
- [ ] Diagnose OpenIPMI failures and establish whether IPMI hardware/functions are needed for the desired readings ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status|T2]]).
- [ ] Interpret SMART values and trends and report any justified disk action ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status|T4]]).
- [ ] Check dependencies and remove the confirmed accidental nic1 entry on pve-7450 as a separate configuration change.
- [ ] Discover the missing router/switch/port/DHCP details and explain the access-policy options ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|Networking]]).

Dropout investigation: [[Projects & Learning/HomeLab/Node Issues/Tasks|Node Issues — Tasks]]. Metrics foundation and later dashboard work: [[Projects & Learning/HomeLab/Monitoring/Tasks|Monitoring — Tasks]]. Career Ops migration/failover: [[Projects & Learning/HomeLab/Project Hosting/Tasks|Project Hosting — Tasks]]. Future service provisioning: [[Projects & Learning/HomeLab/Shared MCP Servers/Tasks|Shared MCP Servers — Tasks]].
