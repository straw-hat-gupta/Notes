# pve-storage — Historical Dropout Evidence

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]] · [[Projects & Learning/HomeLab/Node Issues/Open Questions|Open Questions]]

Collected 2026-10-28, approximately 10:42–10:49 MDT (16:42–16:49 UTC). Read-only SSH inspection of `pve-storage` only. Times in the evidence tables are UTC; `mono` is seconds since the identified boot.

## Assessment

The retained history contains one unexplained journal ending on **2026-06-20 at 20:04:50 UTC**, followed by a different boot later that day. There is no retained shutdown sequence or kernel fault identifying its cause. A host hang, hard reset/power interruption, or missing final log writes remain possible. This is a candidate incident to correlate with peer observations, rather than a confirmed diagnosis.

The **2026-08-23 19:25–19:26 UTC** cluster transitions are different: the local log records a Corosync service restart during a package upgrade, then an orderly system reboot. The **2026-10-28 15:07 UTC** restart is also orderly and follows an upgrade. Those events provide useful controls; they do not explain every reported powered-on dropout.

No retained NIC hang, NIC link-down, OOM kill, panic, lockup, PCIe/AER fault, or block-I/O error signature was found in the kernel-transport scan. That limits the evidence for those causes; it does not exclude a fault that prevented its own logs from reaching disk.

## Coverage and timestamp limits

| Source | Coverage / records examined | Limits |
| --- | --- | --- |
| Journal boot inventory | 13 retained boot IDs; `212.7M` of active and archived journals as reported by journalctl | Retained coverage is not proof that every historical boot or final write survived |
| Kernel transport | 14,288 entries across all retained boots | `_TRANSPORT=kernel` also includes some userspace messages written to the kernel log |
| Corosync | 2,400 entries across all retained boots | Includes startup, peer maintenance, service restarts, and shutdown controls |
| Proxmox management / HA / watchdog units | 72,021 entries across all retained boots | Message-pattern summaries are selective; counts are not a count of outages |
| June 20 terminal window | All 20 entries from 19:49:50 to the last entry at 20:04:50 UTC; complete boot also checked for later monotonic continuation | No later entry under that boot ID; seven mail-delivery records omitted from excerpts |
| August 23 targeted window | All 1,054 journal entries from 19:10 to the retained ending at 19:26:20 UTC | Package-generated compatibility/audit messages grouped rather than repeated |
| October 28 targeted window | All 907 entries from 14:50 to the retained ending at 15:07:39 UTC | Includes other cluster members leaving; a peer departure alone is not a local hardware fault |
| APT | `history.log`, `.1.gz`, `.2.gz`, `.3.gz`; seven retained transactions | APT timestamps are local wall time and have no boot IDs; historical clock corrections apply |
| dpkg | `dpkg.log` (1,283 lines), `.1` (1,175), `.2.gz` (31), `.3.gz` (8,473) | Oldest rotated file includes installation-era 2025 timestamps; not a clean chronological clock |
| Proxmox task index | All 122 retained index entries | Index metadata, not full task payloads; retained index is not an audit of all shell activity |

There is no retained local boot between the orderly ending on August 23 and the next retained boot on October 27. The evidence does not establish whether the machine stayed off, failed to complete that reboot, ran without retained logs, or experienced a separate failure during that interval.

Early wall-clock timestamps are unreliable in several boots. Chrony confirms large corrections, including two boots starting with September 2025 timestamps and one starting with April 2026 timestamps. Boot ID plus monotonic time is the primary within-boot ordering; corrected wall time and independent peer records are needed for cross-node correlation.

## Retained boots

The ranges below reproduce recorded wall-clock values, including clock errors. “Orderly ending” means a retained shutdown/journal-stop sequence, not proof of the reason it was requested.

| Label | `_BOOT_ID` | First recorded UTC | Last retained UTC | Ending / clock context |
| --- | --- | --- | --- | --- |
| S01 | `597144da23984355b296ede39615b30c` | 2026-05-08 23:37:49 | 2026-05-08 23:38:09 | Orderly ending |
| S02 | `c56b45fc721c4aeda6b0b8eb57d6c400` | 2025-09-03 18:38:20 | 2026-05-09 01:48:53 | Clock stepped +21,364,579.056882 s at mono 18.676606; orderly ending |
| S03 | `237e3a1194ea4600a1890478c84e5e7b` | 2026-05-09 02:00:51 | 2026-05-09 02:06:17 | Orderly ending |
| S04 | `7886d82025ea4581b05b0c975c5114e0` | 2026-05-09 02:06:46 | 2026-05-09 20:55:28 | Orderly ending |
| S05 | `75b4cf75838d4e90b902ef12e699822b` | 2025-09-03 18:38:20 | 2026-05-09 21:58:05 | Clock stepped +21,438,795.485465 s at mono 19.235065; orderly ending |
| S06 | `977f75f8a2ad425c8dd3ca508a90f16d` | 2026-05-09 21:58:34 | 2026-05-09 22:03:31 | Orderly ending |
| S07 | `98a41fd711974d3489a8bf4a15ac9910` | 2026-05-09 22:04:00 | 2026-05-09 22:17:04 | Orderly ending |
| S08 | `247f8c101ef24f8fa895865b21c52f52` | 2026-05-09 22:17:34 | 2026-05-13 22:15:46 | Orderly ending |
| S09 | `a683b3f215464b4a976a3b72355d89c7` | 2026-05-28 03:19:27 | 2026-05-28 23:02:26 | Clock stepped −13.663874 s at mono 18.027271; orderly ending |
| S10 | `bfdf9d00fe26403389df2d09c64bc825` | 2026-05-28 23:02:56 | 2026-06-20 20:04:50 | No retained shutdown sequence; candidate unexplained stop |
| S11 | `b2d9eaf685db470ea27568e31fe5dac7` | 2026-04-13 19:38:05 | 2026-08-23 19:26:20 | Clock corrected on June 20; orderly reboot ending on August 23 |
| S12 | `9cc26f94db3f457faadd9edf489a60f5` | 2026-10-27 21:41:35 | 2026-10-28 15:07:39 | Clock stepped −44.882601 s near startup; orderly reboot ending |
| S13 | `ce9a77078d8f4599a7b82237059256da` | 2026-10-28 15:08:09 | Ongoing during collection | Kernel `7.0.14-26-pve` |

## June 20 — unexplained terminal boundary

Boot S10 was running kernel `7.0.2-7-pve`. The final 15 minutes contain nine routine metric-collector lifecycle messages, seven deferred mail-delivery messages, and four routine Proxmox worker messages. There are zero kernel-transport entries in that terminal window. A complete scan of S10 found no entry with a monotonic timestamp after `1976517.055332` seconds.

| UTC | Boot | Mono (s) | Retained event |
| --- | --- | --- | --- |
| 2026-06-20 19:34:03.939003 | S10 | 1974670.785086 | Kernel: `ata3.00: configured for UDMA/133` following SATA-link/ACPI-command messages; no I/O-error or reset signature |
| 2026-06-20 19:59:10.960357 | S10 | 1976177.806439 | `Finished prometheus-node-exporter-apt.service - Collect apt metrics for prometheus-node-exporter.` |
| 2026-06-20 20:04:50.180367 | S10 | 1976517.026450 | pvedaemon: `worker exit` |
| 2026-06-20 20:04:50.206934 | S10 | 1976517.053017 | pvedaemon: `worker 2950580 finished` |
| 2026-06-20 20:04:50.209167 | S10 | 1976517.055249 | pvedaemon: `starting 1 worker(s)` |
| 2026-06-20 20:04:50.209250 | S10 | 1976517.055332 | pvedaemon: `worker 2964614 started` — final retained entry |
| Recorded 2026-04-13 19:38:05.436984 (wrong clock) | S11 | 3.390926 | Kernel `7.0.2-7-pve` starts under a new boot ID |
| 2026-06-20 20:49:49.641614 | S11 | 102.613620 | Chrony: `System clock was stepped by 5879404.981935 seconds` |

Using the corrected S11 timestamp and monotonic time gives an approximate S11 boot start of **20:48:07 UTC**, about 43 minutes after S10's last retained log. That is an inference from the clock correction, not an independently recorded power-on time.

No retained APT transaction or dpkg change is dated near this June 20 boundary. The absence of orderly shutdown markers distinguishes S10 from the maintenance controls below. The final worker replacement is routine and does not establish that pvedaemon caused the stop. The host-side log cannot distinguish a full host freeze, a reset/power event, or lost final records; peer timing and an incident date are still needed.

## August 23 — package restart and orderly reboot

APT records `apt-get dist-upgrade` from **13:22:54 to 13:25:48 MDT** (19:22:54–19:25:48 UTC). dpkg records Corosync `3.1.10-pve2 → 3.1.10-pve3`, libknet `1.31-pve1 → 1.35-pve1`, PVE manager `9.2.3 → 9.2.11`, and installation of kernel `7.0.14-12-pve`.

All events below are in boot **S11**, `_BOOT_ID=b2d9eaf685db470ea27568e31fe5dac7`.

| UTC | Mono (s) | Event |
| --- | --- | --- |
| 19:25:05.463412 | 5524618.435418 | `Stopping corosync.service - Corosync Cluster Engine...` |
| 19:25:05.485174 | 5524618.457180 | Corosync: `Node 4 was shut down by sysadmin` |
| 19:25:06.300556 | 5524619.272562 | `Corosync Cluster Engine exiting normally` |
| 19:25:06.311725 | 5524619.283731 | `Starting corosync.service - Corosync Cluster Engine...` |
| 19:25:06.671762 | 5524619.643769 | New membership `(4.15d)`, local member 4 joins |
| 19:25:08.825547 | 5524621.797553 | New membership `(1.161)`, peers 1, 2, 3, 5 join |
| 19:26:08.042923 | 5524681.014929 | logind: `System is rebooting.` |
| 19:26:12 | Not present in task index | Proxmox `stopall` task recorded `OK` |
| 19:26:13.190710 | 5524686.162717 | HA-LRM: `got shutdown request with shutdown policy 'conditional'` |
| 19:26:18.649292 | 5524691.621298 | Corosync: `Node 4 was shut down by sysadmin` |
| 19:26:19.465869 | 5524692.437875 | `Corosync Cluster Engine exiting normally` |
| 19:26:20.765438 | 5524693.737444 | `Reached target reboot.target - System Reboot.` |
| 19:26:20.765482 | 5524693.737488 | `Shutting down.` |
| 19:26:20.953964 | 5524693.925971 | `Journal stopped` — last retained S11 entry |

There is no NIC hang, link-down, panic, OOM, or I/O-error signature in the targeted 19:10–19:40 window. The brief membership loss near 19:25:06 is explained by the recorded service restart; the 19:26:18 departure is part of the recorded reboot sequence. The records do not establish why there is no retained successful boot immediately afterward.

## October 27–28 — time correction, update, and reboot control

| UTC | Boot | Mono (s) | Event |
| --- | --- | --- | --- |
| 2026-10-27 21:41:05.693872 | S12 | 18.422447 | Chrony steps clock `−44.882601` s; early kernel timestamps therefore appear later than corrected membership/startup records |
| 2026-10-28 15:02:35.684196 | S12 | 62508.412772 | `Token has not been received in 2531 ms` |
| 2026-10-28 15:02:40.654044 | S12 | 62513.382619 | Membership `(1.1bb)`: peer 3 left; not evidence of a local storage NIC failure |
| 2026-10-28 15:04:14–15:06:47 | S12 interval; APT has no boot ID | Not present in APT | `apt-get dist-upgrade` completes |
| 2026-10-28 15:07:26.902135 | S12 | 62799.630710 | logind: `System is rebooting.` |
| 2026-10-28 15:07:31 | Task index; no boot ID | Not present in task index | Proxmox `stopall` task records `OK` |
| 2026-10-28 15:07:35.144160 | S12 | 62807.873 (rounded) | watchdog-mux: `got terminate request` / `clean exit` |
| 2026-10-28 15:07:37.695918 | S12 | 62810.424493 | Corosync: `Node 4 was shut down by sysadmin` |
| 2026-10-28 15:07:39.042039 | S12 | 62811.770614 | `Reached target reboot.target - System Reboot.` |
| 2026-10-28 15:07:39.180627 | S12 | 62811.909 (rounded) | `Journal stopped` |
| 2026-10-28 15:08:09.374646 | S13 | 3.217428 | New boot, kernel `7.0.14-26-pve` |
| 2026-10-28 15:08:19.461237 | S13 | 13.304020 | `e1000e ... nic0: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx` |

The update changed PVE manager `9.2.11 → 9.2.24`, libknet `1.35-pve1 → 1.35-pve2`, and installed kernel `7.0.14-26-pve`. The final Corosync connection/quorum errors occur after its service-stop request, while the host is already shutting down. They are shutdown effects in this window, rather than evidence that quorum loss triggered this reboot. “Shut down by sysadmin” identifies Corosync's administrative shutdown path; it does not identify a person or prove which UI/command requested the reboot.

## Repeated patterns and negative controls

Counts are over retained records, not unique incidents.

| Pattern | Count / coverage | Interpretation |
| --- | --- | --- |
| `nic0: NIC Link is Up 1000 Mbps Full Duplex` | 13, one per retained boot | Consistent startup control |
| NIC link-down, e1000e hardware-unit-hang/reset, `NETDEV WATCHDOG`, transmit-queue timeout | 0 matched kernel-transport entries | No logged local NIC failure signature; no guarantee against an unlogged hang |
| OOM kill, panic/oops/BUG/call trace, soft/hard lockup or hung-task signature | 0 matched kernel-transport entries | No retained host-fault signature for these classes |
| PCIe/AER error, block I/O error, filesystem corruption/error, ATA/NVMe reset or I/O-error signature | 0 matched kernel-transport entries | Separate from the recurring ATA capability/ACPI notices below |
| `ata3.00: Invalid log directory version 0x0000` | 13, once near boot mono 3 s in every retained boot | Startup recurrence, including healthy S13; not localized to a dropout |
| ATA ACPI NOP rejection, ata3 exact message | 68 | Also occurs during ordinary startup/runtime disk activation; no associated logged block-I/O fault found |
| `watchdog: watchdog0: watchdog did not stop!` | 8 | Each in an orderly shutdown sequence; followed by systemd-shutdown taking a 10-minute watchdog |
| `Using hardware watchdog 'Software Watchdog'...` / `Watchdog running with a hardware timeout of 10min.` | 8 of each | Shutdown watchdog controls; not proof of watchdog expiry or hardware BMC presence |
| Kernel priority 0–3 entries | 10 total: 8 watchdog-stop notices and 2 ATA log-directory notices | Most ATA log-directory messages have a different priority; full-text scan found all 13 |
| Corosync missed-token notices (`2531 ms`) | 22 | 2 in S10, 19 in S11, 1 in S12; not unique outage count |
| Corosync KNET peer `link ... is down` | 96 | 4 in S09, 4 in S10, 83 in S11, 2 in S12, 3 in S13; includes peer maintenance |
| Corosync new memberships | 67 | Includes joining, leaving, service restarts, and ordinary shutdown |
| HA-LRM cluster-filesystem connection-refused message | 52 | Last occurrence 2026-05-28 03:51:51 UTC in S09; early setup/quorum context, not a retained June 20 terminal fault |

Current-boot NIC counters from `ethtool -S nic0` show zero receive/transmit errors, CRC errors, collisions, and transmit timeouts. These counters reset with the driver/boot and cannot describe an earlier incident.

## Watchdog and management context

At collection, `corosync`, `pve-cluster`, HA-LRM, HA-CRM, and `watchdog-mux` were active. `ha-manager status` reported quorum OK and `fencing standby (CRM watchdog standby)`; `/cluster/ha/resources` was empty.

The watchdog identity is **Software Watchdog**, with a current sysfs timeout of **10 s**. Systemd reports `RuntimeWatchdogUSec=0` and `RebootWatchdogUSec=10min`. `/etc/default/pve-ha-manager` contains only the commented `ipmi_watchdog` example. No retained self-fence/expired-watchdog signature was found in the reviewed HA/watchdog units. An active watchdog-mux or a shutdown warning alone does not establish that HA reset the host.

`/sys/fs/pstore` was empty. No crash record was available there. Absence of a record does not prove that no crash occurred.

## Package and task controls

Retained APT transactions include upgrades on May 8, May 28, August 23, and October 28; node-exporter/lm-sensors installation on May 30; and iperf3 installation on June 1. None is dated near June 20's terminal boundary. Historical clock anomalies also affect package and task timestamps, so the retained record alone cannot exclude shell work or unlogged maintenance.

The 122 task-index entries comprise 100 `aptupdate`, 12 `startall`, 6 `stopall`, 2 cluster joins, and 2 console-shell tasks. Four May 9 `startall` tasks were interrupted. One August 12 `aptupdate` ended with exit 100; that is a package-index update failure, not evidence that the node hung. The two console tasks failed in early May 28 setup context. Successful `stopall` entries at August 23 19:26:12 UTC and October 28 15:07:31 UTC align with the orderly shutdown controls.

## Confidence and remaining limits

| Conclusion | Confidence |
| --- | --- |
| August 23's short Corosync flap occurred during an orderly service restart in the package-update window | High |
| August 23 and October 28 terminal departures include orderly reboot sequences | High |
| June 20 S10 has an unexplained retained journal ending followed by a different boot | High for the boundary; cause undetermined |
| A replacement NIC, PSU change, or shared D1/storage fault is established by these host-side records | Not established |
| A specific historical powered-on failure is fully explained | Not established without incident identification and peer correlation |

Incident dates, local-console behavior, the June 20 recovery circumstances, and the August-to-October retention/power state remain in [[Projects & Learning/HomeLab/Node Issues/Open Questions|Open Questions]]. No hardware, firmware, network, package, service, or workload configuration was changed.

## Commands and handling

- `hostname`, `uname -r`, `date -u --iso-8601=seconds`, `journalctl --list-boots` (text and JSON), `journalctl --disk-usage`, `last -x -F -w`.
- `journalctl --all --no-pager -o json _TRANSPORT=kernel`; an additional priority `0..3` pass; all retained `corosync`, `pve-cluster`, `pvedaemon`, `pvestatd`, `pveproxy`, `pve-ha-lrm`, `pve-ha-crm`, and `watchdog-mux` unit records.
- Per-boot JSON tails (5–8 entries), complete S10/S11 scans for boundary/clock checks, and explicit UTC windows for June 20, August 23, and October 28. `__REALTIME_TIMESTAMP`, `__MONOTONIC_TIMESTAMP`, and `_BOOT_ID` were preserved in reviewed excerpts.
- All retained `/var/log/apt/history.log*`, `/var/log/dpkg.log*`, and `/var/log/pve/tasks/index` files, with gzip archives read in memory. Package and task results were summarized rather than copied wholesale.
- `systemctl show` for service state and systemd watchdog settings; `ha-manager status`; `pvesh get /cluster/ha/resources --output-format json`; read-only watchdog identity/timeout and default HA configuration; `ethtool -S nic0`; listing of `/sys/fs/pstore`.

All SSH/journal/package/task commands completed without a command error. Initial broad output previews exceeded display limits, so compact recounts and exact-window queries were used for the reported counts/excerpts. Counts above were not capped. Exploratory first/last examples were capped at 4 entries per pattern/boot, initial abnormal samples at 12–14 per class, and per-boot terminal samples at 5–8 entries; exact windows and complete S10/S11 scans resolved the relevant boundaries. Email addresses and unrelated mail contents, console command payloads, and external NTP addresses are excluded from this note. No raw log dump was saved.
