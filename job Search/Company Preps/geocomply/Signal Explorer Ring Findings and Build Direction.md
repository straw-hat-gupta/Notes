---
created: 2026-11-09
updated: 2026-11-09
type: project-findings-and-proposal
status: Proposed direction, not yet committed or built
tags:
  - geocomply
  - case-study
  - fraud
  - signal-explorer
---

# Signal Explorer ring findings and build direction

This note records a November 9, 2026 deep read of the Signal Explorer sandbox (HTML code and its embedded data), the QBR transcript and the support shadowing transcript, and the build direction proposed from it. It supersedes the single-account view of `GTH-418864` in [[Fraud Project Directions and CSM Discovery Guide]]: that account is one of nine in a ring.

Related: [[GeoComply Case Study Materials Review by Package]], [[GeoComply Case Study Materials Review]], [[Brady case clarifications]], [[Eleanor correspondence and application context]].

**How to read this note.** Every figure under "Calculated findings" was computed from the data embedded in `Signal Explorer (sandbox).html` (the same 9,120 checks as `transactions.csv`, plus account, device, operator and report tables that exist only in the HTML). All of it is synthetic. Sections marked "Interpretation" are judgment, not data. Nothing here has been validated with the CSM contact or anyone at GeoComply.

## Proposed direction

**Two weight-bearing objects:** Signal Explorer package and the Quarterly business review transcript. The support shadowing transcript supplies guardrails and test cases but is not one of the two.

**What to build:** a live risk queue for the GreenTeam pod that joins identity status, device linkage, location quality and money at stake, groups accounts into cases, and produces a renewal brief.

**Status:** proposed on November 9. Smarth has not yet committed to it. No prototype exists.

## What the sandbox HTML contains

- Views: Overview, Map, Checks, Accounts, Devices, Operator reports, Network, Field guide.
- Embedded tables: 9,120 checks, 605 accounts (540 Betting.com OH, 65 GreenTeam Health OH), 629 devices (597 appear in checks), 83 operator reports, 2 operator definitions.
- Account fields only in the HTML: signup time, signup IP, ID verification status. All 65 GreenTeam accounts are "Verified"; Betting.com supplies no ID status.
- The Network view links accounts through devices, check-time IPs, signup IP and Wi-Fi access points, up to three steps out, capped at 400 nodes. It always shows both operators, even when the operator filter is set.
- The Copilot is scripted. It has specific answers for only two accounts (`61208246` and `GTH-418864`) and generic text for everything else.
- The field guide says the tool is used by "our fraud analysts and account teams".

## Calculated findings

### The GreenTeam ring

| Fact | Value |
| --- | --- |
| Accounts | 9: `GTH-418864`, `-418891`, `-418896`, `-418915`, `-418943`, `-418958`, `-418970`, `-418983`, `-418996` |
| Signup | All nine during the sandbox week (Mon Oct 5 and Tue Oct 6), all between 1 and 4 am Ohio time, each from a different Verizon mobile IP |
| ID verification | All "Verified" |
| Devices | Three Motorola moto g play (2021), Android 11: `ba7e5a16aaabd9c9` (3 GreenTeam + 2 Betting.com accounts), `49031dd358f67b91` (3 + 2), `55ff04cf69b95cf8` (3 + 0) |
| Other GreenTeam members | 56, all signed up long before the week, each on a device used by no other account |
| Withdrawal requests by the ring | 36 requests, $253,894 |
| Passed | 18 requests, $126,648 |
| Declined, Out of Jurisdiction | 18 requests, $127,246 |
| All GreenTeam withdrawal requests | $272,727 requested, $145,481 passed |
| Ring share | 93.1% of dollars requested, 87.1% of dollars passed |
| Other members who withdrew | 13 accounts, 14 requests, $18,833, all passed, all between 9 am and 6 pm |
| Ring withdrawal hours | All between 1 and 5 am Ohio time |
| Places | Cincinnati OH (pass), Covington KY and Newport KY (declined) |
| GreenTeam's reports that week | One: `GTH-418852`, a long-standing member, "Account hold - manual review / large withdrawal". None of the nine. |

**Cross-operator link.** Four Betting.com accounts on two of the three phones (`61211900`, `61211896`, `61211883`, `61211861`) were reported by Betting.com as suspected identity theft between Oct 7 and Oct 10. GreenTeam reported nothing on those devices.

**Location quality.** Of the ring's 18 passed withdrawals, 10 ($67,568) passed on a "Cellular, IP" fix with accuracy between 1,000 and 3,500 m. Passed checks sit at latitude 39.098 to 39.123; declined ones at about 39.07 to 39.08. Every withdrawal by other members passed on a GPS or Wi-Fi fix with accuracy under 1,000 m. The ring repeatedly gets declined and then passes within minutes (for example `GTH-418983`, Thu 02:53 declined in Newport, 02:57 passed in Cincinnati).

**Border handling differs by operator in the data.** Betting.com has 75 "Too Close to Border" checks (27 accounts, Toledo and Cincinnati, accuracy 804 to 3,948 m) and zero passes in Cincinnati with accuracy over 1,000 m. GreenTeam's checks have only two statuses: Pass and Out of Jurisdiction.

**Replay of a simple rule.** Rule: once a second verified GreenTeam member appears on a device, hold withdrawals on that device. Replaying checks in time order, it fires on the three phones at Wed 01:41, Wed 03:51 and Wed 03:53 Ohio time. $61,924 had passed before it fired; $83,557 of the $126,648 passed afterwards. It touches 9 of 65 GreenTeam accounts, and none outside the ring.

### Betting.com's 82 reports collapse into six groups

| Group | Reported | Detail |
| --- | ---: | --- |
| Six Intel Macs (Web SDK, device IDs ending `-C02F7A`) | 45 | 45 accounts, all reported. Signup IPs `71.66.214.90` (20), `71.66.214.91` (15), `24.166.30.7` (10). Signups in bursts at 1 to 2 am Ohio on Wed, Thu and Fri. Filed as id theft (28), device sharing (10), deposit fraud (4), geolocation violation (3), across Oct 8 to 11. Their 203 checks: 136 Pass, 26 Mock Location, 25 Impossible Travel, 16 Shared Device Limit. |
| One Samsung Galaxy J7 (`16644484ada39bbb`) | 18 | 24 accounts on the phone, Dayton, AT&T Wireless. Six unreported: `61209950`, `61209929`, `61209899`, `61209932`, `61210006`, `61209982`. |
| The Motorola phones shared with GreenTeam | 4 | See above. |
| One iPhone 8 (`C0208EE8…`) | 2 | Six accounts in one evening: Bucharest on a Romanian ISP, then datacenter IPs with VPN/Proxy and Mock Location, then Impossible Travel. Two reported as geolocation violation; four unreported (`61210061`, `61210101`, `61210110`, `61210132`). |
| Suspected identity theft with clean signals | 12 | One device each, T-Mobile, GPS fixes, all "Trusted", no shared device or signup IP. Nothing in the location data corroborates the report. |
| Isolated deposit fraud | 1 | `61211771`, eight passes in Youngstown. Its signup IP `107.198.44.120` is shared with four unreported accounts. |

45 of the 92 Betting.com accounts that signed up during the week are the Mac group; 47 of the 92 signed up between 1 and 3 am Ohio.

### Other checks

- **Campus cluster.** IP `164.107.92.18`: 373 checks, 40 accounts, 40 devices, 30 access points, all Pass, Saturday 13:10 to 17:48 Ohio time. None of the 40 signed up during the week and none is in a report.
- **Blocked accounts.** 269 of 540 Betting.com accounts had at least one failed check; 58 of those are in reports. By accounts affected: Insufficient Location Data 94, Location Services Disabled 82, VPN/Proxy 46, Shared Device Limit 39, Mock Location 33, Too Close to Border 27, Remote Desktop 24, Impossible Travel 17, Out of Jurisdiction 3.
- **Confidence flag conflicts.** 149 checks where `is_trusted` disagrees with `trusted_reason` (confirms the earlier count).
- **Scripted Copilot.** For `61208246` it calls the campus cluster "a common indicator of a coordinated fraud ring" and suggests "reviewing all 40 accounts for suspension". For `GTH-418864` it says "Overall this account appears low risk" and suggests confirming the member's address.

## What the transcripts supply

**QBR (June 18, synthetic).** Leo Martin on GreenTeam: fake member accounts whose "ID documents check out fine" while device and location signals show "same few devices, odd locations"; overnight bot signups; the identity team and security team use "separate dashboards, separate people". Renewal starts in Q3; a new CFO from a bank is running a vendor review with a brief to cut spend 15%, and the pod has not met him. Priya Nair's homework: a 60-second answer on why each account gets its money's worth "in their CEO's words", and one upstream problem to "kill".

**Support shadowing (September 16, adapted from a real session).** The most common operator question is why a player was blocked, answered from Signal Explorer. Benign readings named: a family sharing one tablet, people who live near a state line. Operators send weekly lists of suspended accounts; support passes them to fraud analysts, who investigate in Signal Explorer. The Ashgrove and Marigold cases are IDComply knowledge gaps with no matching data in the Explorer package.

## Interpretation

- The Explorer data appears to have been written to contain the GreenTeam problem the QBR describes: verified identities, a few shared devices, odd locations, overnight signups. The earlier guide treated the QBR and Explorer as unrelated events. The safer framing is that the pattern Leo described is visible in the sandbox week, not that the two form one historical sequence.
- The campus cluster looks like a game-day crowd (Saturday afternoon, university network). That is an inference; nothing in the data says so.
- GreenTeam's rules may lack a border buffer for high-value actions. This is inferred from the absence of a "Too Close to Border" status in its checks, not stated anywhere.
- Earlier AI-assisted reviews in this vault found one ring account and the campus IP but not the ring's size or dollar share. That gap is usable as a "what the LLM missed" example in the presentation.

## Proposed build

1. Replay the week as a stream, so alerts fire when they would have fired. The data is static; "live" means a replay clock.
2. Group accounts into cases by device and signup IP, with dollars attached.
3. Check benign explanations before alerting. The campus cluster must stay quiet; the family tablet and state-line examples from the support transcript become test cases.
4. Give each case an action and an owner (hold withdrawals on a device, tell the operator about unreported linked accounts, review the border rule).
5. Generate the renewal brief: what the location check stopped, and what joining identity with device signals would have added.

**Removal test.** Without Explorer there is no evidence. Without the QBR there is no reason to join identity with device signals, no audience, and no output format.

## Open questions for the CSM contact

1. When an operator sends its weekly suspended list, what goes back to them? Does anyone tell them about linked accounts they missed?
2. Can GeoComply tell one customer that a device was reported by another customer, and in what form?
3. How do CSMs assemble the value story for a renewal today, and how long does it take?
4. Who would act on an alert like this: the fraud analyst, the CSM, or the customer's security team?
5. Who owns a customer's location rules, such as a border buffer on high-value actions?

## Limits

- Withdrawal amounts are requests. The data does not show settled payments or losses.
- Operator reports are the operator's labels, not confirmed fraud. "Verified" is the operator-supplied status.
- The replay rule was chosen after seeing the data and tested on the same single week. It is a demonstration, not a detection rate.
- Cross-operator visibility in the sandbox does not establish that GeoComply may show one customer another customer's reports.
- The analysis scripts are temporary and were kept outside the vault. Figures should be recomputed when the prototype is built.
