# D1 and storage — independent witnesses

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]] · [[Projects & Learning/HomeLab/Node Issues/Open Questions|Open questions]]

Read-only observations on 2026-10-28, 10:42–10:49 MDT. Witnesses: `pve-d2`, `pve-6420`, and Prometheus in monitoring LXC 201. All timeline times below are **UTC**; subtract six hours for America/Edmonton (MDT) on these dates. Node IDs: D1 = 1, storage = 4.

## Findings

- D2 and E6420 independently recorded D1 leaving the cluster on August 17, September 3, and September 29. The first two witness loss times line up with the D1 hardware-unit-hang records from the target-host investigation; September 29 has both retained metrics and target logs.
- On September 29, D1's Corosync peer link, node-exporter endpoint, and Proxmox API became unavailable within the same 15-second period. The surviving cluster still had members 2, 3, and 5. This was broader than an isolated Proxmox web-interface failure.
- D1's final 30 minutes of retained metrics show modest CPU/load and no sustained memory or I/O pressure. The Ethernet carrier and error counters did not change before the last successful sample. A sudden NIC/driver failure after that sample remains compatible with these readings.
- The storage loss at August 23 19:26 was a controlled reboot in the target-host logs. Its earlier 19:25 cluster flap was a Corosync restart during an upgrade. These are maintenance events, not evidence that storage had D1's failure.
- On June 20, E6420 lost contact with all four other members and became a one-node, non-quorate component. This establishes isolation/partition from E6420's view, not that all four other hosts failed. It does not isolate storage's NIC as the cause.

KNET “link down” means a **Corosync peer transport link**, not proof that Ethernet carrier dropped. Exporter/API failure establishes failed scrapes from monitoring, not physical power state or a local-console hang.

## Witness coverage and clocks

| Witness | Retained coverage / continuity | Clock evidence |
| --- | --- | --- |
| pve-d2 | Journals include May 9–October 28. Relevant August boot: `ec51c5268c53465e85dec0f3a6ab61dd`; September 24 onward: `fc15e6c6b5c94e2797498284d00cf4f9`. Corosync restarted normally October 28 at 15:13:50. | Current timezone America/Edmonton; NTP synchronized. Older boot contains April 13 realtime entries among later records, including when queried with a May 1 lower bound. Historical realtime before synchronization cannot be assumed correct. |
| pve-6420 | Journals include May 8–October 28. May 28–August 23 boot: `118f6b838cfd432bae700d769c9ad8f1`; August 23–October 28: `329639523c0e40bb828ab683bceb6a16`; current: `dcb912b23ad44f8e901eb1a543d0607d`. | Current timezone America/Edmonton; NTP synchronized. Matching August/September D1 membership events agree with D2 within milliseconds. |
| Prometheus | Configured retention `30d`. A raw 40-day query actually returns samples from September 26 12:00 UTC through October 28 16:45 UTC. No August or June metrics remain in these series. | Before the September 29 loss, node-time minus scrape timestamp was +14 ms on D1, +8 ms on D2, and +22 ms on E6420. This includes scrape/processing timing and is not a certified clock-offset measurement. Storage had no sample then. |

Prometheus runtime started October 28 at 15:13:00 UTC; its retained TSDB history predates this process restart. Scrapes are configured every 15 seconds. Raw-sample transition times are bounded by neighboring scrapes, not exact physical failure times.

Common monitoring gaps, also present in Prometheus's own `up` series:

- October 24: last self-scrape 05:11:54.936, next 05:12:54.937 UTC.
- October 28: last self-scrape 15:10:39.937, next 15:13:24.936 UTC. E6420 rebooted during this interval.

These gaps are missing observations. They are not additional evidence of D1/storage failure. Long zero-valued target intervals below exclude these sampling gaps.

## Corosync timeline

The rows show membership leaving and its next retained join. They do not, by themselves, classify a shutdown, restart, or failure. D2 and E6420 both record the main events except the June 20 broad loss, where E6420 provides the reliable independent realtime reference.

| Target / date | Peer / membership loss | Next retained join | Interpretation |
| --- | --- | --- | --- |
| D1 — May 28 | 22:52:26.969 | 22:53:43.468 | About 77 seconds; cause not established here. |
| Storage — May 28 | 23:02:23.455 | 23:03:08.470 | About 45 seconds; cause not established here. |
| D1 — June 1 | 23:33:03.117 and 23:41:48.169 | 23:34:20.720 and 23:43:05.169 | Two short absences; maintenance/failure classification needs target logs. |
| Several peers — June 20 | E6420 sees peer 4 down at 20:07:14.282, peers 2 and 1 down within 5 ms; membership excludes 1, 2, 3, 4 at 20:07:19.993. | Peers 2 and 4 join E6420 together at 20:48:25.034; quorum returns. | E6420 isolation/partition; the other four hosts are not proven failed. No witness event was recorded at storage's last prior journal entry, 20:04:50. |
| D1 — June 25 | 21:44:40.991, 21:52:00.367, 21:59:24.693 | 21:46:08.962, 21:53:25.851, 22:00:39.470 | Three short absences; cause not established here. |
| D1 — August 17→23 | August 17: peer down 20:06:28.818; membership left 20:06:35.010. | August 23 19:07:00.491 | Matches the target boot's first NIC hardware-unit hang at August 17 20:06:30.036. |
| Storage — August 23, short | 19:25:06.443 | 19:25:08.823 | Target logs show normal Corosync exit/restart during upgrade. |
| Storage — August 23→October 27 | August 23 membership left 19:26:18.666; KNET no active link 19:26:20.098. | October 27 21:41:01.552 | The departure follows an administrator-requested reboot in target logs. Long absence alone does not identify a later failure or power state. |
| D1 — September 3 | Peer-down evidence in target logs 00:26:31.797; D2/E6420 membership left 00:26:37.476. | 00:31:13.534 | Matches target first hardware-unit hang 00:26:31.505 and later physical power-key event 00:29:34.251. |
| D1 — September 29→October 27 | September 29: D2 peer down 16:21:11.441; membership left 16:21:16.837. | October 27 20:50:17.782 | Independent metrics below confirm simultaneous exporter/API loss. |

### Selected D2 excerpts

```text
2026-08-17T20:06:28.818357Z [KNET] link: host: 1 link: 0 is down
2026-08-17T20:06:35.010306Z [TOTEM] A new membership (2.14f) was formed. Members left: 1
2026-08-23T19:07:00.491416Z [TOTEM] A new membership (1.158) was formed. Members joined: 1
2026-09-29T16:21:11.441789Z [KNET] host: host: 1 has no active links
2026-09-29T16:21:16.837435Z [TOTEM] A new membership (2.1aa) was formed. Members left: 1
2026-09-29T16:21:16.846513Z [QUORUM] Members[3]: 2 3 5
2026-10-27T20:50:17.782090Z [TOTEM] A new membership (1.1b3) was formed. Members joined: 1
```

D2 September 29 event boot `fc15e6c6b5c94e2797498284d00cf4f9`: peer-link-down monotonic timestamp `431602239668` µs; membership-left `431607635722` µs. This preserves the event order independently of wall-clock formatting.

### Target-log correlation

Target excerpts and scan coverage: [[Projects & Learning/HomeLab/Node Issues/Evidence/2026-10-28/D1|D1]] and [[Projects & Learning/HomeLab/Node Issues/Evidence/2026-10-28/Storage|Storage]].

| D1 boot ID | First hardware-unit hang | Independent membership loss | Recovery evidence from target investigation |
| --- | --- | --- | --- |
| `f6c6e5cbd3994c42869982732a736ec7` | August 17 20:06:30.035998 | August 17 20:06:35.010306 | Physical power key August 23 19:05:23.966008; rejoins 19:07:00.491416. |
| `57c21bb0202243a08ada0f898c4668a8` | September 3 00:26:31.504593 | September 3 00:26:37.476096 | Physical power key 00:29:34.251298; rejoins 00:31:13.533532. |
| `6b0b199afd67469a8ac5c65314d756d4` | September 29 16:21:12.057644 | September 29 16:21:16.837435 | Physical power key October 27 20:48:39.707071; rejoins 20:50:17.782090. |

For storage, target boot `b2d9eaf685db470ea27568e31fe5dac7` records August 23 Corosync normal exit at 19:25:06.300556, restart at 19:25:06.311725, logind “System is rebooting” at 19:26:08.042923, and node 4 “shut_down_by_sysadmin” at 19:26:18.649292. These precede the independent peer-loss messages and explain these particular departures as maintenance.

Storage's older boot `bfdf9d00fe26403389df2d09c64bc825` ends June 20 20:04:50. E6420's broad peer loss begins about 2 minutes 24 seconds later, with storage and D2 rejoining at 20:48:25. Target clock correction around 20:49:49 is later than that independent rejoin; it is not the physical boot-start timestamp.

## Prometheus down/up evidence

Fixed evaluation time: `2026-10-28T16:45:00Z`. Raw range selectors return the original 15-second scrape samples; no resampling or five-minute lookback was used to construct these intervals.

| Target / job | Last successful sample before long loss | First failed scrape | Last failed scrape | First successful scrape |
| --- | --- | --- | --- | --- |
| D1 node_exporter | September 29 16:21:07.411 | September 29 16:21:22.411 | October 27 20:50:07.410 | October 27 20:50:22.410 |
| D1 proxmox API scrape | September 29 16:21:02.393 | September 29 16:21:17.393 | October 27 20:50:17.392 | October 27 20:50:32.392 |
| Storage node_exporter | No successful sample before loss in retained coverage | Already failed at first retained sample September 26 12:00:10.011 | October 27 21:40:55.011 | October 27 21:41:10.011 |
| Storage proxmox API scrape | No successful sample before loss in retained coverage | Already failed at first retained sample September 26 12:00:04.801 | October 27 21:41:04.814 | October 27 21:41:19.816 |

Independent PVE node-state series scraped through E6420 agree: `pve_up{id="node/pve-d1",instance="10.44.0.52"}` changes from 1 at September 29 16:21:02.442 to 0 at 16:21:17.442, then returns to 1 at October 27 20:50:32.442. Storage is already 0 at the first retained sample, September 26 12:00:02.442, and returns to 1 at October 27 21:41:17.442. Queries through D2 give the same long-loss/recovery pattern.

### October 28 — separate from the historical failures

| Target | First failed node-exporter scrape | Last failed scrape | First successful scrape |
| --- | --- | --- | --- |
| D1 | 15:07:22.410 | 15:08:37.410 | 15:08:52.410 |
| Storage | 15:07:40.011 | 15:08:10.011 | 15:08:25.011 |
| D1 | 15:15:07.410 | 15:16:22.410 | 15:16:37.410 |

Corresponding reported boot times change, so these intervals include boots/reboots. They must not be merged with the historical hang episodes merely because scrapes failed. D2 also reports a brief D1 Corosync leave/rejoin at 15:05:24.709→15:05:28.015, without an exporter-down interval at 15-second resolution.

| Node | Boot times visible in retained exporter samples (UTC) |
| --- | --- |
| D1 | September 3 00:30:59; October 27 20:50:03; October 28 15:08:29; October 28 15:16:24 |
| Storage | October 27 21:40:47; October 28 15:08:06 |

## D1 resource and link readings before September 29 loss

Thirty-minute windows ending `2026-09-29T16:21:00Z`; rates use one-minute windows with 15-second subquery resolution.

| Reading | Result |
| --- | --- |
| Minimum MemAvailable / MemTotal | 13.64% |
| Maximum load1 | 0.80 |
| Maximum average non-idle CPU | 15.24% |
| Maximum CPU pressure waiting rate | 0.001818 s/s (0.182%) |
| Maximum memory pressure waiting rate | 0 s/s |
| Maximum I/O pressure waiting rate | 0.001289 s/s (0.129%) |
| `nic0` carrier-change increase | 0 |
| `nic0` receive/transmit error increases | 0 / 0 |
| `nic0` receive/transmit drop increases | 0 / 0 |
| Minimum `nic0` network_up | 1 |

These are returned metric values, not substitutes for absent series. Storage had no retained metrics around its June/August departures, so equivalent pre-incident resource checks are unavailable.

## Commands and queries

SSH commands on D2 and E6420 only:

```sh
date -u '+%Y-%m-%dT%H:%M:%S.%NZ'
timedatectl show -p NTPSynchronized -p Timezone
journalctl --list-boots --no-pager
journalctl -u corosync --since '2026-05-01 00:00:00 UTC' --until '2026-10-29 00:00:00 UTC' --no-pager -o json
```

The JSON journal review retained `__REALTIME_TIMESTAMP`, `__MONOTONIC_TIMESTAMP`, `_BOOT_ID`, and `MESSAGE`; membership filters select target IDs 1 and 4. Focused D2 windows: August 17 19:50–20:20, August 23 18:45–19:20 and 19:20–19:32, September 29 16:10–16:35 UTC. Focused E6420 window: June 20 19:55–21:00 UTC. Broader membership scans also preserve short May/June departures.

Read-only HTTP endpoints on `http://10.44.0.80:9090`:

```text
GET /api/v1/status/runtimeinfo
GET /api/v1/status/flags
GET /api/v1/status/tsdb
GET /api/v1/targets
GET /api/v1/label/__name__/values
GET /api/v1/query?query=<URL-encoded PromQL>&time=<UTC evaluation time>
```

Metric names and labels were discovered before querying. `up` is scrape success, while `pve_up` with `id="node/..."` is a node state reported through the Proxmox exporter.

Raw history queries, fixed evaluation time `2026-10-28T16:45:00Z`:

```promql
up{instance=~"10.44.0.(50|54)(:9100)?",job=~"node_exporter|proxmox"}[40d]
pve_up{instance="10.44.0.52",job="proxmox",id=~"node/pve-(d1|storage)"}[40d]
```

The following 30-day queries were also run around October 28 16:43:50 UTC, including the self-scrape gap check and D2 cross-check:

```promql
up{job="prometheus"}[30d]
node_boot_time_seconds{instance=~"10.44.0.(50|54):9100"}[30d]
pve_up{job="proxmox",instance="10.44.0.51",id=~"node/pve-(d1|storage)"}[30d]
```

Pre-loss queries, evaluation time `2026-09-29T16:21:00Z`:

```promql
min_over_time(node_memory_MemAvailable_bytes{instance="10.44.0.50:9100"}[30m]) / node_memory_MemTotal_bytes{instance="10.44.0.50:9100"}
max_over_time(node_load1{instance="10.44.0.50:9100"}[30m])
max_over_time((1-avg by(instance)(rate(node_cpu_seconds_total{instance="10.44.0.50:9100",mode="idle"}[1m])))[30m:15s])
max_over_time(rate(node_pressure_cpu_waiting_seconds_total{instance="10.44.0.50:9100"}[1m])[30m:15s])
max_over_time(rate(node_pressure_memory_waiting_seconds_total{instance="10.44.0.50:9100"}[1m])[30m:15s])
max_over_time(rate(node_pressure_io_waiting_seconds_total{instance="10.44.0.50:9100"}[1m])[30m:15s])
increase(node_network_carrier_changes_total{instance="10.44.0.50:9100",device="nic0"}[30m])
increase(node_network_receive_errs_total{instance="10.44.0.50:9100",device="nic0"}[30m])
increase(node_network_transmit_errs_total{instance="10.44.0.50:9100",device="nic0"}[30m])
increase(node_network_receive_drop_total{instance="10.44.0.50:9100",device="nic0"}[30m])
increase(node_network_transmit_drop_total{instance="10.44.0.50:9100",device="nic0"}[30m])
min_over_time(node_network_up{instance="10.44.0.50:9100",device="nic0"}[30m])
node_time_seconds{instance=~"10.44.0.(50|51|52|54):9100"} - timestamp(node_time_seconds{instance=~"10.44.0.(50|51|52|54):9100"})
```

## Confidence and limits

Confidence is high for the D1 peer-loss/exporter-loss timing and its alignment with target e1000e hang reports. The evidence narrows the failing path but does not distinguish a physical NIC defect from driver/firmware behavior or another condition affecting that device. Storage's June 20 event remains broader and less specific; its August 23 departures are accounted for by controlled maintenance.

The surviving witnesses cannot establish whether a target console still responded, whether a switch port retained carrier, or which physical component failed. Current NTP synchronization does not repair old realtime anomalies. No E7450 SSH or separate incident investigation was included. Remaining questions belong in [[Projects & Learning/HomeLab/Node Issues/Open Questions|Open Questions]].
