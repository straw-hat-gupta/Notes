# D1/storage evidence manifest

[[Projects & Learning/HomeLab/Node Issues/D1 and Storage Evidence|Main evidence report]]

Assembled UTC: 2026-10-28T16:56:43+00:00. Investigation scope: D1/storage historical dropouts, with D2/E6420/Prometheus witnesses. No E7450 access, live changes, active reproduction, or passive monitoring.

## Saved artifacts

| File | Bytes | SHA-256 |
| --- | ---: | --- |
| Baseline.json | 149,525 | `849d49597339337017fe994d85ded4eefa20074f42ecdcd106135afd467a9bd3` |
| Verification.json | 13,086 | `6b92b5a648a53fabf5a8be54562d8a1061e06191a4f2ec7760dde44197425ee4` |
| D1.md | 19,471 | `4da0c9bae4ed4cfc4e149fefaa0035359e09e0e1b49321dd7ef1d74a97177dce` |
| Storage.md | 18,944 | `d5a220eb0ed50ee77275edfbdf906e6c449729b818a6b68be824439748c38dc0` |
| Witnesses.md | 15,768 | `ed95434f5a21142b48c8fd6deb6dba3aefecbf40a4b95459c14a1ad7d70061cf` |
| D1 and Storage Evidence.md | 17,853 | `1e40573429c87dffa4fff16d37335f30381d50239371372b28673347050ff4a5` |

The main evidence report is in the parent Node Issues folder. Hashes identify these reviewed saved artifacts, not forensic images of the original journals. Original logs remain on the hosts and are subject to their normal retention.

## Collection and handling

- `Baseline.json`: per-command invocation, UTC start, stdout/stderr, and exit status for the two targets, plus selected read-only configuration and crash-record availability. Primary snapshot starts approximately 2026-10-28 16:42:45 UTC. Full SMART identity/serial fields were excluded.
- `Verification.json`: independent narrow-window re-queries with exact boot IDs, bounds, UTC and monotonic timestamps. D1's selected-event window is complete for its filter (19 other matches and 12 hang messages, three representative hangs saved). Storage uses a narrowed shutdown/restart filter, with all 16 matching events saved. A larger exploratory storage preview showed 90 of 374 selected entries; it is not the saved verification set.
- The three source notes document broader journal scans, grouped counts, retained boots, exact excerpts, controls, query bounds, and display limits. Exploratory previews were not treated as complete negative evidence; narrow recounts/queries support the reported findings.
- Only relevant reviewed excerpts and diagnostic output were saved. Credential-bearing configuration, private keys, mail contents/addresses, and unrelated console command payloads were excluded. No raw journal export or packet capture was saved.
- Node clock corrections, monitoring gaps, lack of switch-port/console evidence, and unavailable pre-September metrics limit attribution. A missing log message is not proof that its failure class never occurred.
- Collection errors/partial results are retained rather than replaced with zero values. D1 Toshiba SMART exit 64 denotes a historical device-error-log record while overall status is passed; this is not a failed collection or a proven dropout cause. Sensor stderr includes unavailable readings. No kernel/driver setting was changed to obtain results.
