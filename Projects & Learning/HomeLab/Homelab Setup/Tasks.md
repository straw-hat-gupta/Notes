# Homelab Setup — Tasks

[[Projects & Learning/HomeLab/Homelab Setup/Homelab Setup|Homelab Setup]] · [[Projects & Learning/HomeLab/Homelab Setup/Open Questions|Open Questions]]

## Recorded

- [x] Verify hardware against all five live nodes, including pve-d1 GPU and SSD details.
- [x] Record current VM/container placement and each workload's purpose; keep unverified application details in Open Questions.
- [x] Record the installed storage layout and network hardware.
- [x] Identify the purchased replacement NIC models and record D1's ASUS ROG Strix GTX 1070 with 8 GB VRAM.
- [x] Confirm backup/share status: no backups established and no existing external storage shares/clients.
- [x] Record the TrueNAS storage plan and the host-version alignment decision from [[Projects & Learning/HomeLab/ANSWERS|ANSWERS]].

## Storage and protection

- [ ] Confirm existing data to preserve before changing the storage-node disks ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|S2]]).
- [ ] Choose TrueNAS VM versus bare-metal deployment, physical-disk access, and the spare SSD's role ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|S4]]).
- [ ] Prepare the TrueNAS/striped-pool/share configuration and rollback plan for review before installation.
- [ ] Define backup sources, schedule, retention, and an independent/offsite copy; set up the agreed backups and test a restore ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|S1]]).
- [ ] Define datasets and share access for backups, Linux ISOs, shared data, and the proposed network drive ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Storage|S5]]).

## Hosts and faults

- [ ] Confirm where the replacement NICs are installed, if anywhere ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Hardware|H1]]).
- [ ] Prepare a staged Proxmox/kernel alignment plan with backup/rollback and validation before updating nodes ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Configuration|C1]]).
- [ ] Diagnose llm-gpu's NVIDIA driver failure and prepare the smallest repair ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status|T1]]).
- [ ] Diagnose OpenIPMI failures and determine whether the service is needed ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status|T2]]).
- [ ] Review SMART meanings and trends and decide whether any disk action is needed ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Status|T4]]).
- [ ] Check the unused nic1 entry on pve-7450 before proposing cleanup ([[Projects & Learning/HomeLab/Homelab Setup/Open Questions#Networking|N2]]).

Dropout investigation: [[Projects & Learning/HomeLab/Node Issues/Tasks|Node Issues — Tasks]]. Dashboard work: [[Projects & Learning/HomeLab/Monitoring/Tasks|Monitoring — Tasks]]. Portable hosting and failover: [[Projects & Learning/HomeLab/Project Hosting/Tasks|Project Hosting — Tasks]].
