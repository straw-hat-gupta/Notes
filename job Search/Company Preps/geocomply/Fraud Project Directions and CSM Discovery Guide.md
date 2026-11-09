---
created: 2026-11-09
updated: 2026-11-09
type: project-discovery-reference
status: Validate recurring customer problem before choosing a build
tags:
  - geocomply
  - case-study
  - fraud
  - customer-discovery
---

# Fraud project directions and CSM discovery guide

This guide identifies the most useful case packages for a technical fraud-related project, investigates concrete directions, and provides questions for a nontechnical Customer Success Manager. Its purpose is to help Smarth choose a recurring customer problem worth solving and establish what a small working solution should do.

**My starting recommendation:** Investigate the quality of fraud investigation evidence and the handoff from an investigation to a customer or another team. The case provides unusually good examples of misleading interpretations, fragmented context, and unresolved outcomes. A focused tool that checks evidence and prepares a complete next action fits Smarth's experience in operational workflows, validated data, monitoring, and reliable AI integrations. Validate the actual recurring gap before choosing this direction.

**Strong alternative:** An IDComply review tool that combines conversion, fraud outcomes, vendor behavior, and cost to explain which customer/cohort needs attention and what evidence an owner should inspect next. This has stronger aggregate data for measurement, but a basic pass-rate dashboard would overlap with existing capabilities.

**What is established and what is not:** The supplied scenarios and datasets demonstrate exercise problems. Public product pages describe advertised capabilities. Neither proves a particular unresolved problem exists today across GeoComply customers. The CSM's value is to supply concrete workflow evidence: a recent example, a repeated step, the people affected, the current workaround, and what a useful improvement would change. A CSM can validate customer pain and usability; a fraud analyst or technical owner should validate fraud conclusions and production feasibility.

Related references: [[GeoComply Case Study Materials Review by Package]], [[GeoComply Case Study Materials Review]], [[Brady case clarifications]], [[Eleanor correspondence and application context]], and [[GeoComply_Graduate_Rotational_Program_Technology|Graduate Technology job description]].

## Start with these decisions

Before choosing an implementation, answer these five questions in order:

1. Which person has the recurring problem: a CSM, support specialist, customer fraud analyst, integration engineer, or someone else?
2. What happens repeatedly: collecting evidence, interpreting a result, escalating a case, configuring a response, explaining value, or learning from resolved cases?
3. What is still difficult after the existing tools have produced their result?
4. Can the case materials demonstrate that specific problem and a meaningful improvement without internal systems access?
5. What observation would make us abandon the idea because it is already solved, too rare, or impossible to evaluate?

The goal is a technical solution to an observed workflow, not a requirement to invent a new fraud model. Data validation, evidence retrieval, state tracking, contextual analysis, and a usable interface can all constitute substantial engineering.

## Which packages matter most

Package numbers match the ten-object review, rather than the number of files in each folder.

| Priority | Package | Why it matters for this goal | What to take from it |
| --- | --- | --- | --- |
| Read first | 7 Signal Explorer | Strongest check-level fraud investigation evidence and two contrasting interpretation failures | Data inputs, linked entities, uncertainty, and concrete evaluation examples |
| Read first | 5 Quarterly business review transcript | Connects technical signals to customer outcomes, disconnected teams, and commercial consequences | A specific customer decision and the consequences of failing to follow through |
| Read first | 6 Technical support shadowing transcript | Shows recurring customer questions, missing knowledge, and multi-team handoffs | Who does the work, which evidence is needed, and what a complete resolution means |
| Read next | 8 IDComply Data | Supports quantitative investigation of conversion, vendor behavior, signal groups, cost, and observed fraud | Baselines and a second major technical direction |
| Read next | 2 Product Landscape Orientation | Helps locate the proposed tool within existing products and customer workflows | Product boundaries, end-user friction, and what is already offered |
| Supporting fraud reasoning | 3 Pig-butchering white paper | Explains why multiple signals and competing explanations matter | Investigation principles; not a training dataset or proof that an Ohio cluster is a scam operation |
| Customer discovery context | 9 Vertical pipeline extract | Shows integration, ownership, permission-prompt, and purchasing obstacles | Why an apparently useful fraud feature may fail to get adopted |
| Strategic context | 1 The Story So Far | Explains the move toward industries that need a demonstrable reason to buy | The business value of reducing fraud without excessive friction |
| Conditional | 4 Match Ready | Relevant if the CSM identifies peak-event investigation or alert-response problems | Operational readiness; it has no raw fraud-alert or capacity telemetry |
| Presentation context | 10 About the Intern Program | Explains initiative, business value, evidence, and ownership | How to substantiate the contribution, rather than a source of fraud signals |

## Focused package reviews

### Package 7 Signal Explorer

**Files:** [DATA_DICTIONARY.md](<materials/Signal Explorer Package/DATA_DICTIONARY.md>), [transactions.csv](<materials/Signal Explorer Package/transactions.csv>), and [Signal Explorer (sandbox).html](<materials/Signal Explorer Package/Signal Explorer (sandbox).html>).

This package is the best starting point for investigating what a person sees, concludes, and does during a fraud review. The CSV supplies 9,120 check records, including account/device relationships, network and location evidence, the result of the check, confidence fields, and some financial-action context. The HTML also contains account metadata, device metadata, operator definitions, reports, and scripted Copilot responses. Brady confirmed the intended CSV delivery is consolidated; there is no outstanding request for four separate metadata CSVs.

The most useful contrast is between two examples:

- **Shared infrastructure that could be over-escalated:** IP `164.107.92.18` has 373 checks from 40 accounts on 40 devices across 30 access points. All of those checks pass. The sandbox Copilot suggests considering suspension of the group. The evidence instead requires examining a plausible campus-network explanation; sharing an IP is not evidence that forty accounts share one device or one owner.
- **A verified identity that could be under-escalated:** `GTH-418864` has six passes among eight checks, but its device is shared by three health accounts and two betting accounts. The two betting accounts have operator reports categorized as suspected identity theft. There are passing withdrawal requests totaling $14,025 and rejected jurisdiction-related requests totaling $12,429 for the health account. These are requested amounts, not proven losses or settled payments. The Copilot's low-risk reassurance omits important context.

Both examples were rechecked against the current supplied records for this guide. They can test whether a tool retrieves relevant facts, distinguishes evidence from inference, and presents competing explanations. They cannot establish a population-wide fraud detection accuracy.

**Technical opportunities:** Reconstruct a bounded evidence trail; distinguish shared network from shared device; identify inconsistent fields; require source IDs and reporting windows for claims; separate a location verdict from an investigation recommendation; prepare an evidence-complete handoff.

**Limits to design around:** Operator reports are not confirmed-fraud labels. A shared device can have innocent explanations. Cross-operator visibility in the exercise does not establish production permission to expose another customer's accounts. The prototype should respect a chosen operator scope and make any internal-review scope explicit. A passing location check is not proof of account legitimacy, and a failed check is not proof of fraud.

The CSV contains 1,732 passes with `is_trusted=False` and 149 Boolean/reason conflicts. These are valuable data interpretation tests, not automatic instructions to block 1,732 users. Some timestamps extend beyond the advertised week. A trustworthy tool must show the actual window and handle inconsistent evidence explicitly.

**What the CSM can clarify:** Which similar misunderstandings actually generate repeated customer conversations? Who needs to explain or act on the result? Which part is already handled well by current products? A CSM need not define a detection threshold to answer those questions.

### Package 5 Quarterly business review transcript

**File:** [Meeting Transcript_ Quarterly Business Review Readout (Notes by Gemini).docx](<materials/Meeting Transcript_ Quarterly Business Review Readout (Notes by Gemini).docx>).

The most relevant scenario is GreenTeam: identity checks appear satisfactory while device/location behavior and overnight activity suggest another problem. Different customer teams look at different dashboards. Heavy product use makes the account appear healthy, but that does not establish effective fraud prevention or renewal safety.

The important problem is the gap between having a signal and having someone use it. For a project, possible interventions include a review that makes evidence across functions visible, an explicit next-action owner, or a check that a customer-facing explanation actually answers the question raised. Whether this is a real recurring gap must be established with the CSM.

Stawks contributes another pattern: successful work is partly trapped in Slack and Jira rather than becoming a reusable approach. Betting.com's closed self-exclusion ticket demonstrates that correct product behavior does not guarantee the customer's problem is solved. Self-exclusion is primarily a compliance/player-protection workflow in this exercise; it should not be relabeled as fraud detection just to fit the project theme.

TV.NZ shows the difficulty of delivering stronger location evidence when the customer objects to end-user permission prompts. It is relevant to adoption and friction. The packet does not provide actual TV.NZ traffic or a measured proxy-detection dataset, so it is weak support for building a new streaming-fraud detector.

**Technical opportunities:** Connect evidence to an accountable response, check for an unresolved customer outcome at closure, or turn a completed resolution into a reusable, reviewed workflow.

**Limits:** The meeting is synthetic. It supplies requirements and scenarios, not labeled records or measured handling times. Its June conversation is not the same event as the October Explorer checks. Names such as GreenTeam can guide exercise context, but they do not justify joining unrelated datasets or claiming a historical causal chain.

**What the CSM can clarify:** Does the bottleneck occur before investigation, when interpreting findings, when coordinating a decision, or after delivery? Which person owns the result, and who can approve a change?

### Package 6 Technical support shadowing transcript

**File:** [Meeting Transcript_ Technical Support Shadowing (Notes by Gemini).docx](<materials/Meeting Transcript_ Technical Support Shadowing (Notes by Gemini).docx>).

The repeated question in this scenario is why a user was blocked. Support translates check-level evidence into something a customer can understand and routes work between teams. That is directly relevant to fraud-related service delivery, even when the correct explanation is a location or integration issue rather than fraud.

The Harbourline example also shows what a complete operational change looks like: customer context, CSM and legal approvals, staging and production handling, deployment coordination, and before/after evidence. It is an organization-access change, not a fraud-investigation procedure; its exact approvals should not be copied indiscriminately into every fraud case. Its transferable lesson is that a useful handoff contains the required context and evidence for that particular action.

The Ashgrove and Marigold examples show how recurring questions arise from undocumented integration behavior and different staging behavior. More search cannot recover a fact that was never captured. The Ashgrove date example contains a direction-of-age inconsistency, so it should be used to motivate unambiguous input handling, not as a proven reproduction of a particular bug.

**Technical opportunities:** A case intake/evidence validator, a narrow troubleshooting test suite, or a reviewed resolution-capture workflow. These can reduce repeated questions without making unauthorized account decisions.

**Limits:** Brady intentionally excluded the 1,200-row support-ticket CSV. There is no ticket corpus for measuring real resolution times, training a classifier, or mining actual recurring subjects. A workflow prototype must use the supplied scenarios and clearly labeled additional examples. The transcript's 24-hour commitment is for a meaningful response, not resolution of every case within 24 hours.

**What the CSM can clarify:** Which missing information most often produces another round of messages? What does a complete escalation look like? Is the source of repetition missing knowledge, poor retrieval, a customer-specific setting, or unclear ownership?

### Package 8 IDComply Data

**Files:** [IDComply Verification _ Support Tickets_.docx](<materials/idcomply_case_pack [SYNTHETIC]/IDComply Verification _ Support Tickets_.docx>), [verification funnel](<materials/idcomply_case_pack [SYNTHETIC]/idcomply_verification_funnel_SYNTHETIC_v2.csv>), [vendors](<materials/idcomply_case_pack [SYNTHETIC]/idcomply_vendors_SYNTHETIC.csv>), [vendor funnel](<materials/idcomply_case_pack [SYNTHETIC]/idcomply_vendor_funnel_weekly_SYNTHETIC.csv>), and [Core signals](<materials/idcomply_case_pack [SYNTHETIC]/idcomply_core_signals_weekly_SYNTHETIC.csv>).

The documentation defines the data. The customer/week funnel shows conversion stages. Vendor details explain coverage, prices, and latency references. The vendor funnel distinguishes live waterfall checks from calibration samples. Core signals connect verification activity, spend, and thirty-day confirmed-fraud counts for a subset of customers. These five files form one Table object.

For fraud-focused discovery, the Core-signal table is particularly useful. A fresh check gives the following full-period totals across the five customers in that table:

| Signal category | Sessions | Confirmed fraud within 30 days | Confirmed fraud per session |
| --- | ---: | ---: | ---: |
| clean | 474,706 | 1,371 | 0.29% |
| low_confidence | 40,534 | 281 | 0.69% |
| shared_device | 20,476 | 885 | 4.32% |
| vpn_proxy | 17,154 | 1,001 | 5.84% |
| mock_location | 5,112 | 455 | 8.90% |
| out_of_jurisdiction | 8,457 | 154 | 1.82% |

**Calculated finding:** Shared-device, VPN/proxy, and mock-location groups together comprise **42,742 of 566,439 sessions, or 7.55%**, and **2,341 of 4,147 confirmed-fraud outcomes, or 56.45%**. This is a useful concentration for investigating how review effort is allocated. It is not a claim that blocking those groups would prevent 56.45% of losses: the data does not supply losses, interventions, or individual outcomes. Their observed fraud rates are higher than the clean group within each of the five customers too, although that still does not establish causation.

**Coverage correction:** The five customers are Cobalt Sportsbook, Foundry Gaming, Marigold Gaming, Selkirk Interactive, and Tidewater Casino. Pinnacle Play, Rivet Play, and Ashgrove Bet are absent from the Core-signal file. The earlier reviews incorrectly listed Pinnacle in place of Foundry; both have now been corrected. The overall funnel still covers eight customers.

The broader funnel reveals several different patterns: Rivet's gradual deterioration, isolated severe weeks for Ashgrove, and April drops for Cobalt, Marigold, and Selkirk. A fraud-oriented review should ask whether a conversion change coincides with a change in traffic composition, vendor behavior, or document friction; it should not assume every drop is a fraud incident or every improvement is safer onboarding.

**Technical opportunities:** A cohort review that exposes competing explanations, indicates which data is mature enough to interpret, and prepares a specific next investigation rather than only a red health score. A good output could compare conversion, known fraud, and spend for one customer and signal group, with the numerator and denominator visible.

**Limits:** Weekly aggregates cannot reconstruct individual fraud rings. Thirty-day labels cannot be used as if known at the start of the reporting week; a historical early-warning evaluation must exclude future outcomes. There is no snapshot date proving label maturity. Fraud counts are not labeled as fraud among passed sessions specifically. Vendor matches in successive waterfall steps are selected populations; exact reordering benefits cannot be inferred from aggregate match rates alone. The supplied vendor costs are case-model spend, not evidence of a customer's invoice or achievable savings.

### Package 2 Product Landscape Orientation

**File:** [Product Landscape Orientation.docx](<materials/Product Landscape Orientation.docx>).

Use this package to decide where a proposal belongs. Location capture, detection/decision engines, human investigation tools, and adjacent business workflows are different layers. Smarth's strongest fit is likely in investigation, integration, data quality, or operational delivery rather than recreating the underlying location engine.

It also distinguishes the paying customer from the customer's end user. Faster case handling can benefit the operator; fewer unnecessary checks can benefit legitimate users. A change can improve one while harming the other. Any fraud project therefore needs a counter-metric for legitimate-user friction and analyst workload.

**Technical opportunities:** Improve how an existing result is interpreted, checked, integrated, or acted on. Ask the CSM where the current workflow has an observable failure before concluding that a product capability is absent.

**What the CSM can clarify:** Which products customers actually use, which they have but have not adopted, where their own tools take over, and which team controls the decision. Availability, adoption, configuration, and product gaps are separate explanations.

### Package 3 Pig-butchering white paper

**File:** [R3_WP_Pig-Butchering_2024.pdf](<materials/R3_WP_Pig-Butchering_2024.pdf>), especially pages 6–10.

Use the paper for reasoning about combinations of location, concentrated activity, obfuscation, changes in access, and remote control. It helps explain why identity, device, location, and behavior should be considered together. It also supports asking what evidence distinguishes a suspicious pattern from a common benign pattern.

Its strongest contribution is an investigation framework, not a ready-to-use detector. There are no labeled scam-compound records in the case. Country, Wi-Fi concentration, VPN use, or remote desktop alone does not establish wrongdoing. The right technical output is an inspectable evidence chain and a bounded recommendation, rather than a confident claim to identify scam factories.

**What the CSM can clarify:** Which real customer questions involve account takeover, shared accounts, multi-accounting, or suspicious devices; how they explain the signals; and when a specialist must take over. Their experience may be concentrated in gaming rather than financial scams, so establish that scope first.

### Secondary packages and when to use them

The [pipeline workbook](<materials/Vertical_Pipeline_Extract_SYNTHETIC.xlsx>) is useful for asking why a customer does not implement a technically attractive feature. Integration effort, unclear ownership, price, and user friction recur in the synthetic opportunities. The [company story](<materials/GeoComply_ The Story So Far.docx>) supplies strategic context but does not itself identify a validated customer bottleneck.

The [Match Ready article](<materials/Match Ready_ How GeoComply prepares for Major Sporting Events _ GeoComply.html>) becomes important if the CSM reports repeated event-day alert or investigation problems. It does not supply alert logs for proving a new fraud-alerting system. [About the Intern Program](<materials/About the Intern Program.docx>) helps frame initiative and business value; the graduate ownership bar is in Eleanor's correspondence and the job description.

## Check existing capabilities before proposing a replacement

The following public sources were checked on November 9, 2026. They establish advertised capability, not the current entitlement, rollout, configuration, or actual experience of every customer.

| Capability boundary | What the public source says | Consequence for this project |
| --- | --- | --- |
| AI investigation access | The September 29 launch describes MCP access to investigations from AI tools and a built-in Explorer assistant, GeoSentry, with a human reviewer retained. [Announcement](https://www.geocomply.com/news/geocomply-mcp-brings-risk-intelligence-and-decisioning-to-existing-ai-systems/) | A new chat interface alone is unlikely to be a compelling contribution. |
| Investigation workflow | The MCP page advertises linked-entity investigation, bulk lookup, troubleshooting, playbooks, and report handoffs. [MCP product page](https://www.geocomply.com/technology/geocomply-mcp/) | Even a report generator needs a narrower verified gap, such as evidence validation or a failed handoff requirement. |
| Device intelligence | DeviceGuard is advertised as identifying familiar, manipulated, and misrepresented devices across app and browser contexts. [DeviceGuard launch](https://www.geocomply.com/news/geocomply-launches-deviceguard/) | Do not pitch basic device reuse detection as a capability GeoComply lacks. |
| Risk and collaboration | The technology page describes RiskGuard actions, connected-account views, and collaborative case work. [Technology overview](https://www.geocomply.com/technology/) | Validate what remains difficult after existing detection and case tools are used. |
| Identity operations | IDComply advertises waterfall verification, pass-rate reporting, and onboarding support. Its FAQ describes a single customer transaction charge regardless of vendor count. [IDComply product page](https://www.geocomply.com/anti-fraud-and-geolocation-solutions/idcomply/) | A basic funnel dashboard overlaps; vendor cost reductions in the synthetic pack are not automatically operator invoice savings. |

**Inference:** The most promising space may be the quality and operational use of results, or a particular workflow that existing products do not adequately serve. That is a hypothesis for the CSM to test, not proof of an unfilled product gap.

## Technical directions to investigate

The ranking below reflects fit with the supplied evidence and Smarth's background. It is provisional. A concrete recurring example from the CSM should carry more weight than this ordering.

| Direction | Primary user to validate | Available case evidence | Main reason to stop |
| --- | --- | --- | --- |
| A Evidence quality and handoff checker | Fraud analyst, support specialist, or CSM preparing an escalation | Explorer plus a workflow/requirements object | Current tools already meet the relevant evidence and handoff requirements |
| B Fraud-aware IDComply customer review | IDComply operations or a CSM working with fraud analysts | IDComply Data plus a customer-action/requirements object | Customer needs only an existing report, or nobody acts on the proposed review |
| C Fraud-signal delivery conformance tests | Integration/solutions team supporting customers | Explorer plus QBR's disconnected-signal scenario | No concrete mapping or consumer behavior can be specified and tested |
| D Reviewed resolution-to-playbook feedback | Support/product operations | Support transcript plus another substantive evidence object | No permitted resolution examples or recurring knowledge gap to evaluate |

### Direction A Evidence quality and handoff checker

**Recurring problem to validate:** A customer or internal reviewer receives a plausible fraud explanation but still needs another exchange because evidence is missing, ambiguous, contradictory, out of scope, or disconnected from a clear next action.

**Small technical version:** Load the supplied synthetic records, select an account and reporting window, and prepare an inspectable evidence packet. Before marking it ready, run deterministic checks on the claims: correct account/operator, exact counts and time window, shared IP versus shared device, known versus unknown outcomes, conflicting confidence fields, and whether a required next action/owner is provided. Optional generated prose must use that checked evidence; it should not determine the underlying counts or verdict.

The useful difference from another investigation interface is the explicit readiness check: what is supported, what is inconsistent, and what information must be supplied before the recipient can act. Start with one recipient and one handoff format, rather than building a case management platform.

**Demo:** Run the campus example and the linked health example. Show a misleading draft claim, the evidence that contradicts or qualifies it, the resulting review status, and a concise handoff. Demonstrate a missing-data case rather than always producing a complete-looking result. Do not automatically suspend or unblock accounts.

**How to evaluate:** Compare the output with independently checked counts and an explicit claim checklist. Have the CSM assess whether the intended recipient still needs to ask an obvious follow-up; have an analyst assess the reasoning. If comparing handling time, give both versions the same task and information, measure active work separately from waiting, and report who participated. A two-example success is a demonstration, not a measured fraud detection rate.

**Two-object design:** Explorer supplies evidence. A second Table object must materially define a workflow or acceptance contract used by the tool—for example, a transcript-derived requirement that the review explicitly addresses identity/device disagreement and names the next responsible function. Cite the source passage and show the enforced field or test. A transcript mentioned only in the introduction does not satisfy the case requirement. The CSM's interview is valuable validation but is not itself one of the supplied Table objects.

**CSM test:** “When a fraud explanation comes back to you, what is the most common reason you still cannot send it to the customer or close the question? Can you walk me through the last example?”

**Fit with the resume:** Validated data imports, audit history, stakeholder-driven workflows, and testing AI-generated output. It can show technical depth through evidence handling and evaluation without claiming professional fraud expertise.

### Direction B Fraud-aware IDComply customer review

**Recurring problem to validate:** A headline pass rate masks a deteriorating cohort, or a team notices a change but cannot turn it into a focused investigation with an owner and a measurable outcome.

**Small technical version:** Build one customer/cohort review using the actual CSVs. Show the period, conversion stages, signal composition, mature observed fraud outcomes where available, vendor timeouts/spend, and the next question the data supports. Separate observations from explanations and expose unavailable fields. Start with an interpretable comparison rather than an invented composite health score.

**Demo:** Contrast a stable cohort with one that needs review, then show that an isolated vendor issue, document-upload drop, and higher-risk traffic are different hypotheses. For retrospective analysis, label the thirty-day fraud outcomes as later information. A proposed early warning can use only features available at that earlier time and cannot be validated with future labels leaking into its inputs.

**How to evaluate:** Verify customer/week joins, weighted percentages, coverage exclusions, and the distinction between live and calibration checks. Test that missing or immature fraud outcomes display as unavailable, not zero fraud. Ask the CSM to identify a specific next action from the review. The case can measure calculation correctness and task usefulness; it cannot establish a reduction in real fraud losses.

**Two-object design:** IDComply Data supplies the metrics. The QBR or support transcript must contribute concrete operational requirements that alter the generated review and its action workflow—for instance, an action remains unresolved until its customer consequence and owner are recorded. If the second object only motivates a chart, strengthen that dependency before calling this a compliant two-object build. Do not join GreenTeam or Betting.com to the eight IDComply customers.

**CSM test:** “When a customer says verification or fraud performance has worsened, which three pieces of information do you request first, and what decision does each one change?”

**Fit with the resume:** Python ingestion, relational data, monitoring, and user-facing operational tools. Keep the central outcome fraud/risk investigation; pure conversion optimization would move away from the stated interest.

### Direction C Fraud-signal delivery conformance tests

**Recurring problem to validate:** Different teams or downstream systems interpret a passed location or identity result as permission to proceed, while additional risk context is not surfaced or acted on as intended.

**Small technical version:** Create an explicit, illustrative consumer contract and replay selected supplied records through it. Keep location result, identity result, confidence, evidence quality, and review recommendation separate. Show when a required field is missing, a value conflicts, or a consumer collapses several meanings into one “pass.” A failed test should identify the exact record and unmet expectation.

**Demo:** Show a deliberately simplified consumer that treats location pass as a complete risk decision, then a consumer that preserves the distinctions and routes ambiguous cases for review. Mark both as demonstration consumers; neither is evidence of GeoComply's production API implementation. The 1,732 pass/not-trusted checks and 149 confidence conflicts are useful fixtures, not labeled fraud examples.

**How to evaluate:** Test explicit mappings and expected behavior, including missing fields and no access to another operator's data. Use an analyst/solutions engineer to review the contract. The CSM can validate the customer symptom but cannot certify a production API schema or decision policy.

**Two-object design:** The QBR supplies the identity/security disconnect requirement and Explorer supplies the replay evidence. The requirement must be a testable input to the demonstration, not merely a quote. A real integration adapter requires an actual supported contract, which is not supplied.

**CSM test:** “Have you seen a customer misunderstand what a successful check guarantees? What did they do with that interpretation, and who had to correct it?”

**Fit with the resume:** API integration, validation, production diagnostics, staged releases, and tests. This is a strong alternative if the contact describes a concrete integration misunderstanding rather than an analyst-interface problem.

### Direction D Reviewed resolution-to-playbook feedback

**Recurring problem to validate:** A useful fraud-related resolution is answered for one customer but does not become reliable guidance for the next similar request.

**Small technical version:** Turn one resolved, synthetic scenario into a structured draft: symptom, evidence, applicable product/environment, proposed action, reviewer, source, and what would make the answer outdated. Keep unreviewed explanations separate from approved guidance. Demonstrate finding a relevant answer and showing why a superficially similar scenario falls outside its scope.

**Demo and evaluation:** Use a few explicit scenario variants and test source traceability, environment applicability, and refusal to fill unsupported gaps. The intentionally omitted support-ticket file cannot become a dependency. The second substantive Table object must contribute actual technical evidence or validation rules, not background prose.

**CSM test:** “What is a question you have answered for more than one customer where the answer still depends on finding the same person or old conversation? Why has the existing documentation/playbook not solved it?”

**Fit and limitation:** This fits documentation and AI workflow experience, but it depends more heavily on discovering a current unsolved workflow. Existing documentation search and playbooks make a generic retrieval assistant a weak pitch. Prefer it only if the CSM can identify a specific missing capture/review loop.

## Directions to deprioritize for this case

- A new general fraud chatbot, graph viewer, or unqualified report generator: substantial existing product overlap.
- A new device fingerprint, VPN detector, or automatic account-blocking model: the packet lacks the required production signals and reliable labels for validating it.
- A model claiming to detect pig-butchering compounds from Ohio check records: the supplied evidence does not support that claim.
- A bot detector inferred from the QBR's overnight-signup anecdote: there is no corresponding labeled signup-event stream in the pack.
- A live, cross-customer intelligence service: exercise visibility is not production authorization, and real operational data is unavailable.
- A ticket-mining project dependent on the excluded 1,200 records: Brady explicitly removed that dataset from scope.
- A vendor-waterfall optimizer promising a precise improvement: aggregate outcomes do not identify all overlap and counterfactuals.
- A self-exclusion-list product as the main fraud idea: it may be a worthwhile separate compliance problem, but it is not the strongest fit for the stated fraud focus.
