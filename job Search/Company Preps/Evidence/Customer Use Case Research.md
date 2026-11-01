# Evidence customer and use-case research

Research date: **2026-10-31** (America/Edmonton).  
Related: [[Product Review Plan]] · [[Home Lab Analytics - Review Log]] · [[Market Research]]

## Finding

**Public sources establish named organizational adoption and useful workflows, but not Evidence's three largest paying customers or their three most common use cases.** Select review scenarios by the strength of the evidence, and ask Evidence to validate their commercial importance.

The strongest detailed cases found in this search are **Every Cure, Brighthive, and Existence**. These are research selections, not a revenue or deployment-size ranking. The evidence is strongest for an actual released artifact at Every Cure, a described product integration at Brighthive, and declared tool use plus reporting responsibilities at Existence.

Three parallel research agents covered vendor/customer stories, customer-authored evidence, and adoption/edition boundaries. Findings were consolidated against the existing review questions. Research was public and read-only; no customer outreach, account access, or dashboard implementation was performed.

## What can be said about prominent customers?

Evidence's current homepage displays logos including Apple, The Linux Foundation, DC Government, Dialogue, Modern Animal, Clemson Athletics, Victory+, and others. That establishes a vendor association, not the project, current contract, edition, usage scale, or actual reporting workflow. Ambiguous labels such as Apollo or Philadelphia should not be expanded into a specific legal entity without corroboration. Its illustrated customer tables contain demo businesses; they are not Evidence's customer ranking. [Evidence homepage, undated; accessed 2026-10-31](https://evidence.dev/)

Evidence says Core serves thousands of organizations, including several Fortune 100 companies, and Studio serves hundreds. Those are vendor-reported aggregate counts, not audited customer disclosures. [About Evidence, undated; accessed 2026-10-31](https://evidence.dev/about)

The embedded-analytics launch reports unnamed early customers delivering analytics to thousands of their own customers. Those downstream recipients are a different population from direct Evidence accounts; they cannot be mapped to homepage logos from this evidence. [Embedded Analytics as Code, 2025-12-18](https://evidence.dev/blog/embedded-analytics)

## Research shortlist

| Organization | Strongest evidence | Workflow lens | Edition established? | Confidence boundary |
|---|---|---|---|---|
| Every Cure / MATRIX | Engineering release and published dashboard | Dataset-release quality reporting | Evidence framework; current Studio unconfirmed | Actual released artifact; payment and deployment scale unknown |
| Brighthive | CEO interview on company website | Conversational analysis → visualization → team sharing | Explicitly open-source Evidence | Described integration; usage volume and performance unverified |
| Existence | Employer-authored job posting | Recurring product and executive metrics | Unspecified | Declared tool use; responsibilities may include planned work |

Sources and limitations for each row follow. None establishes why the organization selected Evidence over a named competing BI product, or its commercial relationship with Evidence.

### Every Cure — release-specific data-quality reporting

**Documented:** MATRIX's March 6, 2025 release introduced an Evidence dashboard for knowledge-graph composition/connectivity, with a dashboard accompanying each graph release. It documents quality metrics and how adding a knowledge source changed drug–disease connectivity. Engineers and data scientists are credited, but individual dashboard ownership and reviewer permissions are not specified. The technical problem is communicating changes in released data through reusable metrics and visualizations. [MATRIX v0.4.0 release, 2025-03-06](https://docs.dev.everycure.org/releases/2025/03/06/v040/)

**Artifact corroboration:** A researcher retrieved the public report showing version v0.15.37 and an August 13, 2026 update timestamp. It exposes release trends, knowledge sources, normalization, edge validation, and connectivity summaries. Another fetch could not access the same URL; interactions were not tested. A displayed update timestamp does not establish today's refresh cadence. [Published KG dashboard, accessed 2026-10-31](https://data.dev.everycure.org/versions/latest/evidence/index.html)

**Unknown:** Precise audience, review/sign-off process, replaced alternatives, selection rationale, access controls, and measured business outcome. This original release predates Studio; do not use it to claim current Studio adoption.

### Brighthive — AI exploration becomes a shareable report

**Documented:** In a company-hosted CEO interview, Brighthive describes an agent retrieving relevant warehouse data, exploring a user's question, and handing a visualization request to an agent that uses open-source Evidence. Users refine the result conversationally and generate a dashboard to share with teammates. The described audience includes business teams without dedicated analytical expertise. [Brighthive CEO interview, published 2025-03-04; updated 2025-03-06](https://www.brighthive.io/post/brighthive-your-ai-powered-data-team)

**Why this case matters:** It documents Evidence as the output/reporting layer inside another product's analytical workflow. It supports testing iterative analysis and handoff, rather than only static dashboard construction.

**Unknown:** Evidence's selection rationale, replaced BI alternative, current implementation, deployment volume, report permissions, and review/versioning mechanics. The CEO's speed claims concern Brighthive's overall system, not an independently measured Evidence benchmark. Brighthive's downstream clients are not independently established Evidence customers.

### Existence — shared company metrics and recurring reporting

**Documented:** An employer-authored Senior Data Analyst posting explicitly identifies Evidence.dev as a tool Existence uses. It describes a time-intelligence product and daily product reporting plus recurring dashboards for Product, Marketing, Finance, and leadership. The analyst owns metric definitions, reports, analysis, and executive communication; a paired data engineer owns Snowflake, Dagster, integrations, and transformations. Metrics include activation, retention, conversion, cohorts, and acquisition economics. [Existence job posting, absolute publication date unavailable; accessed 2026-10-31](https://www.linkedin.com/jobs/view/senior-data-analyst-at-existence-4471755972)

**Confidence boundary:** This is direct employer evidence of tool adoption and relevant requirements. A hiring description can include work still to be built; it does not prove that every listed report already runs in Evidence. Relative listing dates varied across fetched representations, so no exact publication date is inferred.

**Unknown:** Studio edition, existing report inventory, adoption scale, decision rationale, replaced alternatives, implemented permissions, and measured outcomes. Cross-functional coordination is documented; specific in-product collaboration features are not.

## Additional leads and a useful non-adopter

**Dialogue:** Steve Mercier identifies Dialogue as an early Evidence partner in a public comment on the founder's post. This strengthens the homepage association, but supplies no detailed workflow or edition. Mirrored job descriptions mentioning Evidence alongside Metabase were found; without the original role page, they were not used to attribute particular reports to Evidence. [Founder post and Dialogue comment, stable publication date not established; accessed 2026-10-31](https://www.linkedin.com/posts/activity-7496599824427913216-TNor)

**Flipside:** Its own site describes offering unified reporting built on Evidence.dev. It is a useful implementation-partner lead, but does not establish a named deployed client, edition, or measurable outcome. Do not relabel its general client-experience logos as Evidence customers. [Flipside, undated; accessed 2026-10-31](https://flipside.be/en)

**Fluid Attacks — evaluator, not customer:** Its dependency decision page says it retained D3/Billboard after evaluating Evidence. Its stated concerns are Enterprise licensing for iframe embedding, Studio/GitLab workflow compatibility, and authentication work for OSS. These are buyer-reported assessments, not independently tested current limitations. They are useful questions about operating burden and fit with existing development practices. [Fluid Attacks D3 decision, updated 2026-10-28](https://docs.fluidattacks.com/stack/dependencies/d3)

There is a specific edition question to resolve here: the newer Core announcement describes built-in basic authentication. Do not repeat an evaluator's broad OSS-auth claim as a current product fact without checking which version was evaluated. [Evidence Core, 2026-08-26](https://evidence.dev/blog/evidence-core)

## Edition boundaries for the review

| Milestone | Relevance |
|---|---|
| [Studio launch, 2025-06-06](https://evidence.dev/blog/evidence-studio) | Introduced the browser authoring/AI/governance environment. Older framework adoption does not establish Studio use. The planned end-2025 sunset of the earlier Cloud product is an announced plan, not shutdown confirmation. |
| [Native warehouse support, 2026-06-07](https://evidence.dev/blog/native-warehouse-support) | Vendor describes customers coordinating dbt and reports in one repository/PR and using development warehouse environments. Customers are unnamed. |
| [Deploy previews, 2026-06-23](https://evidence.dev/blog/deploy-previews) | Describes GitHub PR preview links for feedback before publishing. This is a workflow to test, not proof that a particular named customer uses it. |
| [Evidence Core, 2026-08-26](https://evidence.dev/blog/evidence-core) | The shared open-source foundation includes live warehouse queries, reusable metrics, validation, and container self-hosting with basic authentication. Studio adds hosted authoring, email distribution, page access control, its analytics agent, and hosted MCP. |

**Implication for Q1/Q2:** Do not position live queries or reusable metric definitions as uniquely Studio benefits. Test the effort and experience of the whole workflow. Do not apply older browser/static-query limitations to current Core without verification.

## Three walkthroughs to run

**Everything below is proposed test design using synthetic data, not a claim about the customers' exact steps, schemas, thresholds, or installed features.** These are evidence-informed review cases, not the three most popular customer use cases.

### 1. A daily product report with shared metric definitions

**Provenance:** Existence's declared reporting and analyst/engineer responsibilities. Prioritize this as the broad business-reporting test.

**Starting situation:** Product and leadership need one daily report and disagree about what counts as an active user.

**Minimal synthetic data:** `users(user_id, signup_date, channel)`, `events(user_id, occurred_at, event_name)`, and `subscriptions(user_id, start_date, amount)`. Use 30 days, two channels, and a small known set of internal/test users.

**Steps:**
1. Write a definition of daily active users and calculate an expected total independently.
2. Build a KPI report, daily trend, and channel breakdown; reuse the definition on a second report page.
3. Have a second test participant request exclusion of internal/test activity. Review the change and check both pages.
4. Share a reader view through an authorized test account and record how its role differs from the author's.

**Success:** Both reports agree with the expected result after the change. A reviewer can understand what changed; a reader can access the intended report without editing it.

**Evaluate:** Definition reuse, review/publishing effort, role clarity, regression visibility, and whether a teammate can maintain the work. Compare the same revision with an AI-built dashboard. Maps to Q1–Q4 and Q6.

### 2. A versioned data-quality report before a release

**Provenance:** Every Cure's released graph/QC dashboards. This is the closest match to the homelab walkthrough's pipeline-health and freshness concerns, although the domains differ.

**Starting situation:** A new dataset release adds a source; reviewers must distinguish genuine coverage improvement from a data-quality problem.

**Minimal synthetic data:** `release_metrics(release_id, source, category, record_count, invalid_count, connected_count, generated_at)`. Create two versions, three sources, and one deliberate validation regression with known totals.

**Steps:**
1. Build a report showing version, generation time, source coverage, and validation counts.
2. Add a version comparison and narrative explaining the known change.
3. Have another participant inspect the regression, request a revision, and identify which query supplies the displayed result.
4. Publish or preview the revision while preserving a way to retrieve the earlier version.

**Success:** A reader identifies the regression and correct release without relying on the author. Earlier results remain distinguishable, and the correction can be reviewed before replacing the shared view.

**Evaluate:** Parameterization/reuse, historical context, query traceability, reviewer handoff, and confidence that fresh-looking charts reflect the intended dataset. Do not equate code history with retained historical data. Maps to Q1, Q3, Q4, and Q6.

### 3. An open-ended question becomes an iterated, shareable dashboard

**Provenance:** Brighthive's described AI-to-Evidence workflow. Test whether Sam's positive experience in [[Home Lab Analytics - Review Log]] generalizes beyond homelab data.

**Starting situation:** A non-specialist knows the business question but not the appropriate chart or metric.

**Minimal synthetic data:** `activity(date, team_id, channel, active_users)` for six weeks. Include a known weekday pattern, one missing-data day, and one channel with a different trend.

**Steps:**
1. Ask the Evidence agent what changed and which components would make a useful primary report.
2. Check its interpretation against the known pattern and missing-data day. Record any clarification questions.
3. Request a channel filter and a revised metric; inspect and accept the proposed change.
4. Share the saved report with a test participant and ask them to explain the question, filters, methodology, and caveat.
5. Request a later revision and assess how easily the participant understands it.

**Success:** The report represents the known data accurately, makes the missing-data limitation visible, and is understandable and reusable by someone who did not write the original prompt.

**Evaluate:** Useful suggestions, agent intent handling, explanation quality, saved context, acceptance/revision behavior, and sharing. Repeat with a general coding agent using the same data and request to compare effort. Do not assume Brighthive's permissions or agent behavior are Evidence Studio features. Maps to Q1–Q4 and Q6.

## How to capture the results

For each walkthrough, record the task/step, expectation, actual behavior, impact, help/docs visits, and outcome. Preserve raw observations separately from interpretation, following [[Product Review Plan]]. Include smooth interactions and successful handoffs. Compare tools using the same data, task, and completion condition; report setup effort separately from later editing effort.

The current evidence supports hypotheses about reuse, explainable reporting, guided iteration, and handoff. It does not establish that collaboration is the dominant buying reason or that Evidence outperforms Hex/Grafana. Those remain questions for the review.

## Questions to ask Evidence directly

1. Which three customers are most significant by revenue, active readers, or report usage—and which definition should guide this review?
2. What are their highest-frequency, highest-value workflows? Can Evidence provide a demo or anonymized workflow description?
3. Which current Studio customers have documented team-review, publishing, and permission requirements?
4. Why did those customers choose Evidence, what did it replace, and which alternatives remain alongside it?
5. Where do customers get stuck, and what usage/support evidence establishes the impact?
6. How do actual customers divide work among analysts, engineers, reviewers, and readers? How does this map to project/organization roles?
7. Which older framework customers migrated to current Core or Studio? Which capabilities drove that decision?

## Limits and next decision

Public research completed; no verified customer-size ranking or contract information was found. Source dates distinguish historical adoption from current claims. Some pages had inconsistent accessibility or relative dates; no interactive customer-dashboard QA was performed.

Run the three provisional walkthroughs, while asking Evidence to validate that these are representative of commercially important customers. Keep the ongoing homelab observations as personal-use evidence rather than treating them as established customer priorities.
