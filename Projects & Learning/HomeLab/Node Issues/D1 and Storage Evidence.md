# D1 and Storage — Dropout Evidence

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]] · [[Projects & Learning/HomeLab/Node Issues/Open Questions|Open questions]] · [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]]

Investigation date: **2026-10-28**. Historical, read-only review of pve-d1 and pve-storage, with independent D2/E6420 cluster logs and monitoring history. E7450's issue is excluded. No live configuration, service, package, NIC, or power changes were made; no passive monitor or failure reproduction was started.

## Findings

| Target | Finding | Confidence / limit |
| --- | --- | --- |
| D1 | Three retained incidents contain persistent e1000e transmit-ring hangs, loss of peer connectivity and quorum, and recovery following a physical power-key intervention. The OS continued writing logs during isolation. | **High confidence in the network transmit-path failure mechanism.** The physical NIC, driver, firmware, and triggering condition are not isolated from one another. |
| D1 — June 25 | Memory-pressure messages and blocked Proxmox tasks involving FUSE/rw-semaphore waits precede an abrupt journal ending. | **Observed separate host/management stall.** Its underlying cause is unresolved; it has no matching e1000e unit-hang signature. |
| Storage — August 23 | The brief membership flap was a Corosync restart during an upgrade. The subsequent departure followed an explicit reboot request and orderly shutdown sequence. | **Confirmed maintenance mechanism for these departures.** It does not explain a separate reported powered-on/unreachable incident. |
| Storage — June 20 | Its journal ends without a shutdown sequence. E6420 later loses all other peers; storage and D2 subsequently rejoin after restarting. | **Unresolved.** Host hang, reset/power loss, logging loss, or shared-path trouble cannot be distinguished from the retained evidence. |
| Shared cause | Both targets use e1000e, but storage has no retained equivalent of D1's unit-hang signature. | A common NIC fault across both machines is **not established**. |

The evidence supports a **D1-specific transmit-path finding**. Replacing both NICs on an assumed common failure is not justified. The three hangs occurred on the older `7.0.2-7-pve` kernel; both targets now run `7.0.14-26-pve`. No unit hang appears in the short retained upgraded D1 boots, but no durable repair has been validated.

## Symptoms and evidence coverage

The reported symptoms were Proxmox showing a node offline and the host being unreachable despite the chassis remaining powered. Recovery usually involved a manual reboot/power cycle. Exact incident dates were not recalled and the directly attached console was not checked. The log sequences below identify retained events; they cannot map every undated report to a specific incident.

| Source | Coverage / purpose |
| --- | --- |
| [[Projects & Learning/HomeLab/Node Issues/Evidence/2026-10-28/D1\|D1 source review]] | Nineteen retained boots since May 6, journalctl-reported `1.7G` of journal data; per-boot kernel/cluster history, maintenance and shutdown controls. |
| [[Projects & Learning/HomeLab/Node Issues/Evidence/2026-10-28/Storage\|Storage source review]] | Thirteen retained boots, journalctl-reported `212.7M` of journal data; kernel/cluster history, firmware-access limits, maintenance and abrupt-tail analysis. |
| [[Projects & Learning/HomeLab/Node Issues/Evidence/2026-10-28/Witnesses\|Independent witnesses]] | D2/E6420 Corosync membership histories and raw Prometheus samples from September 26 onward. |
| [[Projects & Learning/HomeLab/Node Issues/Evidence/2026-10-28/Baseline.json\|Current baseline]] | Command-level timestamps/exit statuses, versions, boot IDs, networking/counters, quorum, storage and SMART readings at approximately 16:42 UTC / 10:42 MDT. |
| [[Projects & Learning/HomeLab/Node Issues/Evidence/2026-10-28/Verification.json\|Independent excerpt verification]] | Separate exact-window checks of D1's September 29 failure and storage's August 23 maintenance sequence. |

Source file hashes and handling limits are in [[Projects & Learning/HomeLab/Node Issues/Evidence/2026-10-28/Manifest|Manifest]].

Times below are **UTC** unless marked MDT. For these summer/autumn dates, MDT is UTC minus six hours. Retained boot timestamps include large RTC/NTP corrections; within-host ordering uses boot IDs and monotonic time. Cross-host comparisons use synchronized portions of the journals and independent peer observations, not an assumed correct BIOS clock.

## D1 incident timeline

| Incident, UTC (local MDT date) | First unit-hang report | Local quorum loss | Recovery evidence / next peer join |
| --- | --- | --- | --- |
| August 17 (August 17) | 20:06:30.035998 | 20:06:34.998967 | Power key August 23 19:05:23.966008; rejoins August 23 19:07:00.491416 |
| September 3 (September 2) | 00:26:31.504593 | 00:26:37.466083 | Power key 00:29:34.251298; rejoins 00:31:13.533532 |
| September 29 (September 29) | 16:21:12.057644 | 16:21:16.835754 | Power key October 27 20:48:39.707071; rejoins October 27 20:50:17.782090 |

### Repeated NIC signature

| Boot ID | Retained unit-hang messages | First → last unit-hang report, UTC |
| --- | --- | --- |
| `f6c6e5cbd3994c42869982732a736ec7` | 257,370 | August 17 20:06:30.035998 → August 23 19:05:28.019996 |
| `57c21bb0202243a08ada0f898c4668a8` | 92 | September 3 00:26:31.504593 → 00:29:33.518593 |
| `6b0b199afd67469a8ac5c65314d756d4` | 1,217,624 | September 29 16:21:12.057644 → October 27 20:48:38.009625 |

The detector repeats at approximately two-second intervals. These are repeated reports of sustained stalls, not 1,475,086 separate outages. The other sixteen retained boots have no matching unit-hang report.

### September 29 — independently verified sequence

All local entries below are from boot `6b0b199afd67469a8ac5c65314d756d4`.

| UTC | Monotonic µs | Source / event |
| --- | --- | --- |
| 16:21:11.340182 | 2303412215603 | D1 Corosync: peer link to node 2 down; other peer links become unavailable in the same group |
| 16:21:11.441789 | Witness boot timestamp in source note | D2: D1 has no active KNET links |
| 16:21:12.057644 | 2303412933066 | D1 kernel: `e1000e 0000:00:19.0 nic0: Detected Hardware Unit Hang` |
| 16:21:16.834674 | 2303417710095 | D1 membership becomes singleton node 1 |
| 16:21:16.835754 | 2303417711175 | D1 pve-cluster: `node lost quorum` |
| 16:21:16.837435 | 431607635722 on D2 | D2 membership excludes D1 |
| 16:21:17.393 | Scrape timestamp | D1 Proxmox API scrape first fails |
| 16:21:22.411 | Scrape timestamp | D1 node-exporter scrape first fails |

The first KNET symptom precedes the first driver detector message by about 0.72 seconds. The unit-hang report precedes local quorum loss by about 4.78 seconds. This proves temporal alignment of the transmit stall and isolation, not that the detector fired before all network symptoms.

Selected kernel excerpt:

```text
2026-09-29T16:21:12.057644Z
_BOOT_ID=6b0b199afd67469a8ac5c65314d756d4
__MONOTONIC_TIMESTAMP=2303412933066
 e1000e 0000:00:19.0 nic0: Detected Hardware Unit Hang:
   TDH                  <4d>
   TDT                  <e1>
   next_to_use          <e1>
   next_to_clean        <4c>
   next_to_watch.status <0>
```

The same queue/head/tail state remains in subsequent sampled messages while time advances. The source review retains representative entries and exact whole-history counts rather than copying over a million repeated messages.

### Why this is broader than a Proxmox UI problem

D2 and E6420 independently record membership loss. Monitoring simultaneously loses both the node exporter and Proxmox API endpoint, then records recovery after the physical power-key event and new boot. D1 continues local kernel/userspace logging throughout its long isolation windows and accepts the power key through systemd-logind. That contradicts a whole-OS freeze for these three episodes, while remaining compatible with an unusable host network path.

Prometheus's final thirty minutes before the September 29 loss show maximum load1 0.80, approximately 15.24% maximum average non-idle CPU, minimum available RAM 13.64%, and no sustained memory/I/O pressure. Carrier/error/drop counters did not increase before the last successful scrape. The last metric sample precedes the failure; these counters do not rule out an abrupt transmit stall afterward.

### Other D1 history and controls

The reviewed October 28 update/reboot sequences have orderly service shutdown activity and short exporter gaps. They are separate from the sustained hardware-unit-hang episodes. Shutdown-time watchdog warnings also occur in normal controls and do not, by themselves, establish watchdog fencing.

Older June 20/June 25 abrupt journal endings or short absences are not assigned to the e1000e mechanism. June 25 boot `abbb74ff88d249bd90e19d7647370de8` records memory pressure from 21:39:14 UTC and four blocked-task warnings at 21:40:53–21:42:58 UTC. The traces involve pvedaemon/pvescheduler waits, a rw-semaphore associated with pve-ha-lrm, and FUSE operations. The journal ends at 21:43:12 with another memory-pressure message; a peer reports departure at 21:44:40. No OOM kill or physical disk fault is established. This is a separate unresolved host/management-stall mechanism, not evidence that the later NIC hangs were caused by memory pressure. The three strong network sequences do not establish one cause for every historical departure.

## Storage incident timeline

### June 20 — unexplained journal ending and wider partition

Storage boot `bfdf9d00fe26403389df2d09c64bc825` ends at **20:04:50.209250 UTC**, monotonic `1976517055332` µs, with a routine pvedaemon worker message. Its final fifteen minutes contain no retained shutdown request, kernel crash, or incident-specific I/O error. No later entry exists in that boot by monotonic time.

At 20:07:14 UTC, independent E6420 logs lose storage, D2 and D1 peer links; membership subsequently excludes all four peers. This establishes E6420's isolation/partition view, not that all four other machines failed. Storage and D2 rejoin together at 20:48:25.034 UTC.

Storage's next boot starts with an incorrect April date. At monotonic 102.613620 seconds, chrony steps the clock forward by approximately 5,879,405 seconds to June 20 20:49:49.642 UTC. Its boot start is therefore approximately 20:48:07 UTC, rather than the erroneous first realtime timestamp.

**Finding:** an abrupt recording stop followed by a later boot is retained, but the cause is unresolved. Power/reset, host hang, journal loss, and a broader network/power event remain alternatives. No directly matching NIC-hang signature or pre-incident metrics identify one of them.

### August 23 — maintenance departures

All target entries below are from boot `b2d9eaf685db470ea27568e31fe5dac7`.

| UTC | Monotonic µs | Event |
| --- | --- | --- |
| 19:25:05.463412 | 5524618435418 | `Stopping corosync.service` during the recorded package upgrade |
| 19:25:06.300556 | 5524619272562 | `Corosync Cluster Engine exiting normally` |
| 19:25:06.311725 | 5524619283731 | `Starting corosync.service` |
| 19:25:08.825443 | 5524621797449 | Full five-member synchronization restored |
| 19:26:08.042923 | 5524681014929 | systemd-logind: `System is rebooting.` |
| 19:26:18.649292 | 5524691621298 | Corosync: `Node 4 was shut down by sysadmin` |
| 19:26:20.765438 | 5524693737444 | `Reached target reboot.target - System Reboot` |

D2/E6420 observe the short departure/rejoin during the service restart and the later departure after the reboot request. These specific peer losses have a confirmed maintenance explanation. No retained new storage boot appears until October 27; the interval does not establish whether it was powered off, stuck before OS startup, or operating without retained local evidence. It cannot be silently classified as a NIC failure or as a resolved reported incident.

### Storage negative evidence and gaps

The reviewed thirteen-boot kernel history has no matching e1000e unit hang/reset, NETDEV watchdog, OOM/panic/lockup, PCIe/AER, or read/write I/O-error signature. The source note records the search terms/counts. Absence in retained logs is not proof that no such failure occurred while logging was unavailable.

`ata3.00: Invalid log directory version 0x0000` occurs once near startup in all thirteen retained boots, including a healthy current boot. Shutdown watchdog warnings occur in orderly controls. Neither is incident-specific evidence for the reported dropout.

No June/August Prometheus metrics remain. SMBIOS exposes only an invalid firmware-log descriptor, no readable firmware event entries; no usable IPMI device or pstore crash record was found through the inspected interfaces. BIOS event records may still require a physical-console check if they are available there.

## Competing explanations

| Explanation | D1 assessment | Storage assessment / limit |
| --- | --- | --- |
| NIC transmit path / driver | Strongly supported for the three repeated hang sequences. Physical card versus driver/firmware/trigger remains open. | No equivalent retained local signature; replacement is not justified by D1's evidence alone. |
| Cable / switch / shared network | Not isolated experimentally. Persistent queue hangs and repeated same-host patterns narrow the failing path, but upstream triggers are not fully excluded. | June 20 wider partition permits shared-path explanations; no switch-port logs or physical test identify a component. |
| Corosync-only or Proxmox UI | Inadequate as the sole explanation: driver hangs plus independently failed exporter/API access. Quorum loss is consistent with network isolation. | August departures are service-restart/reboot events; the separate reported incident remains unmapped. |
| Whole-host hang / power / watchdog | Contradicted as the explanation for the three strong sequences by continued local activity and accepted power-key events. Older abrupt tails remain unclassified. | Not distinguishable for June 20. An abrupt tail alone does not identify PSU failure; shutdown watchdog notices are controls. |
| Resource exhaustion / boot-disk trouble | No sustained pre-September-29 pressure explains that network incident; June 25 separately has pressure and blocked-task evidence. Physical disk trouble is not established. | No retained OOM/panic/I/O trigger; missing history and metrics limit exclusion. |
| Bridge / addressing / firewall | Current configurations are coherent; no timed change or conflict was linked to the three sequences. Historical negative evidence is not complete exclusion. | Current configuration does not reconstruct an unrecorded past fault. |

## Current target baseline and collection limits

At approximately 10:42 MDT on October 28, both targets were reachable as root, running PVE manager 9.2.24 and kernel `7.0.14-26-pve`. Their nic0 links were 1 Gb/s/full duplex. Both were members of a quorate four-member component, with five expected votes and quorum threshold three. No separate incident involving other nodes was investigated.

Both current NIC snapshots report zero receive/transmit errors and transmit-timeout counts. EEE is enabled but inactive. These are post-reboot counters/settings, not proof that the historical fault is fixed or that EEE caused it. Current short CPU/I/O readings include diagnostic collection activity and are not pre-incident controls.

All six target disks report SMART overall passed. D1's Toshiba boot SSD additionally retains one ATA error record at power-on lifetime 1,125 hours; `smartctl` returns 64 for that historical error-log bit, not a failed overall-health result. Its record is not tied to an incident calendar time and does not establish the dropout cause. [smartctl exit-status definitions](https://github.com/smartmontools/smartmontools/blob/main/src/smartctl.h).

Current reachability after upgrades does not validate a repair. No monitor, stress test, NIC swap, cable/port swap, service restart, or failure reproduction was performed.

## Smallest justified next steps

1. **Protect Career Ops before disruptive D1 work.** Establish and verify an independent backup/restore path for its application data and configuration.
2. **Account for the intervening D1 kernel update before selecting a repair.** The failure mechanism was recorded on `7.0.2-7-pve`; the current kernel is different. If it recurs, prepare a D1-only transmit-path isolation proposal. A spare NIC is a candidate controlled comparison, not proof of a defective onboard adapter. Define one changed variable, preserved IP/bridge/VM networking, physical-console access, downtime, and rollback before requesting approval. Do not combine offload/EEE/NIC changes. Historical first failures occurred roughly 10–53 days into boots, so a short healthy post-reboot check cannot be the durability acceptance test.
3. **Keep storage unresolved.** Do not replace its NIC solely because D1 failed. First map any remembered non-maintenance incident to a date/recovery and check whether the June 20 or post-August-reboot gap is the relevant event.
4. **For the next natural incident, specify evidence before reboot.** From a directly attached console, if responsive: record time/uptime/boot ID, kernel tail, link/counter state, gateway and D2 reachability, and cluster status; compare D2's view and guest reachability. If the console is unresponsive, photograph its state and note power/switch LEDs and the exact recovery action. This is an unstarted follow-up proposal, not an installed capture mechanism.

Remaining uncertainties are maintained in [[Projects & Learning/HomeLab/Node Issues/Open Questions|Node Issues — Open Questions]]. Repairs and validation remain unchecked in [[Projects & Learning/HomeLab/Node Issues/Tasks|Tasks]].
