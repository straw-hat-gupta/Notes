---
created: 2026-11-10
updated: 2026-11-10
type: project-decision-and-build-plan
status: Direction chosen; prototype not yet built; CSM not yet interviewed
tags:
  - geocomply
  - case-study
  - fraud
  - build-plan
---

# Shadow mode value report build plan

**Decision (November 10, 2026):** Smarth chose a GeoComply-run shadow mode as the case direction. GeoComply's customer pod runs rules that combine IDComply and location/device signals on a customer's own data, changes nothing for real users, and brings back the result as a report in the customer's own numbers.

This replaces two earlier candidates: the analyst-facing risk queue in [[Signal Explorer Ring Findings and Build Direction]], and Smarth's operator-facing cross-product rules platform. The evidence behind the choice is in that findings note; the product boundaries are in `materials/Product Landscape Orientation.docx`.

## Why this framing

It keeps the strongest part of Smarth's platform idea (shadow mode) and drops the parts a GeoComply reviewer would attack:

| Critique of the operator-facing platform | How this framing answers it |
| --- | --- |
| Overlaps RiskGuard (user-level risk API on Core data plus ML) and customers' own rules engines | GeoComply runs it internally; going live is a recommendation through existing product settings, not a new engine |
| Too big for "an afternoon or two" | A rule replay, a report and tests |
| GeoComply doesn't hold the customer's money, so "production mode holds withdrawals" overstates it | The report recommends; the customer acts |
| GreenTeam can't be shown Betting.com's reports | Internal tool, so cross-operator evidence stays private to GeoComply |
| A new product clashes with a CFO cutting vendor spend 15% | More value from products GreenTeam already pays for |

It also matches what the QBR praises. On TV.NZ, Priya Nair asks for the leak "in their own numbers" and "a number with the league's name on it". Her homework asks each pod for a 60-second "worth every dollar" answer and one upstream problem to kill.

## Users

- **Uses it:** GeoComply's customer pod: the CSM (Leo Martin in the QBR), with a fraud analyst or data scientist (Mei Lin's role).
- **Reads the report:** the customer's head of security and, at renewal, the CFO.
- **Not a user:** GreenTeam staff do not log in or configure anything.

## The two objects and the removal test

| Object | What it supplies | Remove it and… |
| --- | --- | --- |
| **Signal Explorer package** | Per-check stream for the after-signup rules: accounts, devices, IPs, locations, accuracy, withdrawals, signup times, "Verified" status, operator reports | The after-signup rules have nothing to run on and the GreenTeam case disappears |
| **IDComply Data** | Weekly totals by GeoComply signal with verification passes and 30-day confirmed fraud (5 customers, 26 weeks), replayed by the signup-time rules; also reference fraud rates by signal for the after-signup rules | The signup-time rules have no data and the after-signup rules lose their reference fraud rates |

The QBR is the source of the problem and the audience. It is cited openly but is not counted as one of the two objects.

**Requirement for the removal test to hold:** reference rates must be read from the IDComply file in code, not typed into slides.

## Connectors and rules (first version)

### Signup-time rules on IDComply data

Runs on weekly totals per customer. It cannot evaluate individual sessions.

- **S1** If a session carries `shared_device`, `vpn_proxy` or `mock_location`, send it to a document check or manual review.

Shadow result, all five customers, Feb–Jul 2026 (computed November 10):

| Customer | Sessions | In S1 groups | Share | Passed despite signal | Confirmed fraud, all | In S1 groups | Share |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Cobalt Sportsbook | 126,198 | 9,571 | 7.6% | 4,284 | 939 | 533 | 56.8% |
| Foundry Gaming | 111,500 | 8,392 | 7.5% | 3,562 | 743 | 417 | 56.1% |
| Marigold Gaming | 105,741 | 8,089 | 7.6% | 3,677 | 806 | 443 | 55.0% |
| Selkirk Interactive | 86,772 | 6,504 | 7.5% | 2,958 | 655 | 368 | 56.2% |
| Tidewater Casino | 136,228 | 10,186 | 7.5% | 4,296 | 1,004 | 580 | 57.8% |
| **All five** | **566,439** | **42,742** | **7.5%** | **18,777** | **4,147** | **2,341** | **56.5%** |

Confirmed fraud is 5.48% of sessions in the S1 groups, against 0.29% for clean sessions.

How to word it: S1 adds friction for about 7.5% of sessions, aimed at the groups holding about 56% of confirmed fraud. Do not claim "fraud prevented": the docs don't say the fraud counts are limited to passed sessions, and the 30-day labels are known only later.

### After-signup rules on Explorer data

Replays checks in time order.

- **P1** When a second newly verified member appears on the same device, hold high-value actions on that device. GreenTeam result: fires early Wednesday on the three Motorola phones and flags 9 of 65 members, no others. Of the nine's $126,648 in passed withdrawal requests, $43,091 passed before it fired and $83,557 after.
- **P2** A withdrawal that passes on a fix with accuracy worse than 1,000 m goes to re-check. GreenTeam: 10 of the nine's passed withdrawals ($67,568). No other member's withdrawal meets it. Wording note: a border-distance condition still needs designing.
- **P3 (internal only)** A device carries accounts reported by another operator, so alert the pod. Never shown to the customer.

### Harmless-case controls

These must stay quiet:

- The campus IP `164.107.92.18` (Betting.com): 40 accounts, 40 devices, all pass.
- An authored "family tablet" fixture: two long-standing members on one device with daytime activity. It must be labelled as invented test data.

## The shadow report

One page per customer:

- **Headline in the customer's numbers.** For example: "Combining IDComply with your location checks, P1 would have flagged 9 of 65 new members and held $83,557, with no other members affected."
- **Per rule:** what fired and when, accounts or sessions affected, dollars, legitimate users affected, the reference fraud rate from IDComply with its counts.
- **Caveats:** requests versus losses; operator labels versus confirmed fraud; rates borrowed from gaming customers.
- **Recommendation:** the rule to switch on and who would switch it on. Which existing product or setting carries it is unconfirmed (see open questions).

## Tests and checks

- IDComply signal totals reconcile to the funnel file (130 customer-weeks, sessions and passes match exactly).
- Replay recomputes the known GreenTeam figures ($253,894 requested, $126,648 passed, $127,246 declined; P1 split $43,091 / $83,557).
- Harmless controls produce no flags.
- No rule reads information from after the check it is judging. The 30-day labels are used only as reference rates.
- The customer-facing report contains no other operator's data.

## Suggested stack

Python for loading, rules and replay, with pytest. A static HTML report as the output. Both appear on the brief's list of tools GeoComply uses.

## Out of scope on purpose

- Bot detection: no signup-attempt data.
- A rule builder interface for customers.
- Live production enforcement.
- Joining GreenTeam to IDComply customers.
- A new chatbot.
- Pig-butchering claims.
- The excluded support-ticket CSV.

## Open questions

For the CSM contact:

1. How does the pod prove value at renewal today, and how long does it take?
2. Would a customer accept a report built from shadow rules on its own traffic? Who on their side would read it?
3. When a customer has both IDComply and location checks, do different teams own them?
4. Can a report mention that a device was reported by another customer?
5. Does GreenTeam's "Verified" come from IDComply? (Smarth's working assumption is yes; the QBR doesn't say.)

For the IDComply Product Operations intern:

6. Does IDComply use the location/device signal when deciding pass or fail?
7. Are the 30-day fraud counts limited to sessions that passed?
8. Which product setting would carry a rule like S1 or P1: IDComply step-up, RiskGuard, or something else?

## Limits

- All data is synthetic.
- The rules were chosen after seeing the data and are tested on the same period. They are demonstrations, not detection rates.
- The IDComply customers are gaming operators; GreenTeam is health and pensions.
- In the demo, the per-account identity input is Explorer's "Verified" field, standing in for an IDComply connection the materials don't include.
