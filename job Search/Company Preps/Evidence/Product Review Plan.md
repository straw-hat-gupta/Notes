# Evidence product review plan

Created: 2026-10-31  
Source: Sam's dictated brainstorm and the organized review plan in this chat.

## Purpose and emphasis

**What makes Evidence a better way for a team to build, maintain, and share dashboards and reports—and how clearly does that value come through when using it?**

**Central question, clarified 2026-11-01:** What value does **Evidence provide over Hex**, for which team and recurring use case, and what evidence would make that team choose it? Use competitor research to answer this, rather than letting the review become primarily an explanation of Hex's strengths. Keep Grafana and AI-built alternatives as supporting comparisons.

Focus primarily on usability, using collaboration as the main lens. Features matter when they help or prevent someone from completing a real task. Keep observed behavior, user expectations, hypotheses, and recommendations distinguishable.

**Working synthesis:** [[Product Review Findings]] — the collective intermediate document: key positives, pain points, source evidence, provisional answers, and next investigations. Refine this into the final feedback later.

**Raw case notes:** [[Home Lab Analytics - Review Log]] — chronology and transcripts, HLA-01–HLA-46. The native-agent and Claude/MCP builds, two-account collaboration, and GitHub setup have initial findings; reuse, role isolation, conflict recovery, and meeting/distribution/embed workflows need further testing.

Supporting material: [[Customer Use Case Research]] (provisional scenarios, not a largest-customer ranking) · [[Hex vs Evidence - Product and Growth Research]] (primary-source comparison, growth evidence, and hypotheses; no Hex trial) · [[Claude Dashboard Comparison Prompt]] · [[How I Use AI]].

## Review questions

### Q1 — Why choose Evidence?

**Partially answered:** Data-grounded suggestions and reporting tools showed value. [[Hex vs Evidence - Product and Growth Research#Product comparison|Research comparison]] now distinguishes workflows and deployment/repo options; unique advantage and long-term reuse remain unproven. [[Product Review Findings#Q1 — Evidence's value|Current answer and limits]].

What value does Evidence provide over Hex, Grafana, or a dashboard built with an AI coding tool such as Claude?

For the primary Hex comparison, test candidate advantages in deployment/runtime ownership, maintaining reusable reports and definitions, and fitting a team's existing development/review workflow. For each, identify the buyer constraint, show the task/outcome, and check Hex's equivalent before calling it a differentiator. AI assistance and code-backed projects alone do not establish an advantage.

Starting hypotheses from the brainstorm, not established product advantages:
- A standardized framework and reusable components reduce the work of building dashboards.
- A maintained collection of reports makes future dashboards and changes easier.
- Shared conventions make teammates' reports easier to understand and modify.
- Collaboration, publishing, or access management reduce work around the dashboard itself.

Refinement: an AI-built dashboard can also live in a maintained repository. Test what Evidence adds beyond storing code: reusable components, consistency, maintenance, collaboration, or another benefit.

### Q2 — Why choose Studio over open source?

**Partially answered:** Integrated authoring, preview, acceptance, and co-editing helped; a direct Core comparison remains open. [[Product Review Findings#Q2 — Studio's additional value|Current answer and limits]].

What additional value does Evidence Studio provide compared with using the open-source framework?

- What work does Studio remove, and for whom: author, reviewer, administrator, or reader?
- Which parts of the workflow become easier, and is that benefit discoverable?
- Does Studio meaningfully improve collaboration?
- When would an open-source user have a clear reason to adopt Studio?

### Q3 — How well does collaboration work?

**Partially answered:** Invitation and live editing worked; permissions, review, mixed Git workflows, and recovery need testing. [[Product Review Findings#Q3 — Collaboration|Current answer and limits]].

Follow a report through **create → share → review → revise → publish → maintain**.

- Can I share a dashboard with someone who needs to work on it?
- Can another person understand, reuse, and change what I built?
- How do teammates give feedback, coordinate changes, and recover from mistakes?
- Who can view, edit, publish, and manage access?
- How granular are permissions and roles across workspaces, individual reports, and underlying data?
- Sam prefers connections scoped to individual projects. Establish the current Studio behavior, then test how project scope, optional sharing/reuse, and user permissions would support the intended collaboration boundary; the exact sharing interaction is not yet specified.
- Before publishing, can I tell who will see the change?

### Q4 — How usable is the workflow?

**Answered for the Home Lab walkthrough:** Specific strengths and friction are synthesized; causes and broader prevalence remain provisional. [[Product Review Findings#Q4 — Usability|Current answer]] · [[Product Review Findings#Pain points and candidate improvements|Findings and evidence]].

Where do I feel frustrated, lose confidence, need help, or fail to complete the task?

- Can I discover the next action and understand what it will do?
- Does actual behavior match my expectation?
- When I need documentation, is it easy to find, relevant, and sufficient?
- Is an obstacle caused by discoverability, unclear behavior, a missing capability, or something still unknown?
- Which features or interactions make the workflow especially smooth?
- Would a more agent-centric entry point let a less technical participant complete setup, building, validation, and delivery with fewer handoffs? Sam's proposed broader audience is a hypothesis, not measured demand or a demonstrated reason to choose Evidence over Hex.
- Can I choose the data for a specific investigation, see what the agent actually used, inspect generated logic, and save a useful result as a maintained report? Distinguish source prioritization/prompt guidance from enforced data permissions; test both rather than assuming a selector restricts access.

A documentation visit is a signal to investigate, not automatically a defect. A missing feature can cause a usability problem; the categories can overlap.

### Q5 — Which customer use cases matter most?

**Open pending customer validation and walkthroughs:** Research identifies candidates, not the highest-value workloads or largest customers. [[Product Review Findings#Q5 — Priority customer use cases|Current answer and next evidence]].

Identify three high-value, recurring workflows among major Evidence customers and try them myself.

For each, establish:
- Who authors, collaborates, reads, and administers the result?
- What business outcome are they pursuing, and how often?
- Why did they choose Evidence, and what did they use before?
- What concrete result counts as successful completion?

Use customer conversations or available customer evidence. Do not assume these use cases are known yet. Home Lab Analytics is my exploratory walkthrough; whether it represents a major customer workflow remains unconfirmed.

### Q6 — Where do alternatives provide more value?

**Desk research completed; empirical comparison open:** [[Hex vs Evidence - Product and Growth Research]] covers product value, classic/4.0 release differences, pricing, and documented growth milestones. Growth explanations remain hypotheses; no Hex hands-on test, Grafana comparison, or standalone AI build comparison is complete. [[Product Review Findings#Q6 — Alternatives and Hex growth|Current answer and limits]].

Compare Evidence with Hex, Grafana, and an AI-built dashboard using the same task, data, and completion criteria where feasible.

Compare:
- Time and effort to a useful result.
- Ease of modifying and reusing previous work.
- Collaboration and handoff.
- Publishing and permissions.
- Confidence in ongoing maintenance.

Separate research question: **Why has Hex grown, and what is it doing that Evidence is not?** First verify the growth premise and evidence. Consider product experience, audience, positioning, and distribution; growth alone does not demonstrate a missing feature.

## Practical review process

1. **Establish real customer workflows.** Identify the three priority use cases and their success criteria. Label assumptions until confirmed.
2. **Complete the workflows myself.** Start from a realistic user situation and work toward a shared, useful result. Involve a teammate when testing collaboration.
3. **Capture observations as they happen.** Preserve my wording, task context, expectations, actual behavior, impact, documentation trips, and any workaround or resolution I report. Capture positive experiences too.
4. **Compare the alternatives on equivalent work.** Record differences in effort, friction, collaboration, reuse, publishing, and maintenance.
5. **Turn evidence into recommendations.** Prioritize by customer impact, frequency, and whether the issue blocks completion. Tie each recommendation to an observed task.

## Note-taking agreement

As I dictate observations in this chat, save them in [[Home Lab Analytics - Review Log]] and connect them to the questions above.

- Preserve my original wording in a clearly labeled observation; do not substitute an interpretation for what I said.
- Add a separate interpretation explaining the relevant connection, without forcing every note into every question.
- Distinguish usability friction, positive experiences, missing-capability hypotheses, and value-communication issues. A capability that I cannot find is not yet proven absent.
- Link related observations and record later resolutions without erasing the initial experience.
- Leave severity, cause, reproducibility, and customer relevance unconfirmed unless the evidence supports them.
- Update synthesis as patterns emerge, keeping the chronological record intact.
- Maintain [[Product Review Findings]] as the collective intermediate analysis across use cases. Keep findings concise, link raw evidence, distinguish Sam's reports from agent observations, revise confidence/resolutions as investigations progress, and keep the six answer-status links current. Do not duplicate the chronology there.
- Keep [[How I Use AI]] updated when AI's role changes or a new use emerges. Keep it brief and specific; distinguish work performed from planned research/tests rather than copying the detailed log into it.

## Existing notes to connect

- [[Product Feedback Notes]]: the Docs button led to an external page when an integrated Studio documentation experience was expected. Related to Q4 (expectations and help discovery) and Q2 (Studio experience). Earlier observation; not re-tested in this session.
- [[Product Feedback Notes]]: the Support button on the schedules page reportedly did nothing. Related to Q4 (feedback and access to help). Earlier observation; not re-tested in this session.
- [[Giving Product Feedback]]: customer perspective, unmet use cases, and existing user pain points. Related to Q5 and Q6.
- [[Market Research]]: existing external comments and competitor leads. Treat these as research leads rather than verified product limitations.

## Final review deliverables

1. A clear, evidence-backed explanation of Evidence's value and Studio's additional value.
2. Three customer-grounded walkthroughs with concrete friction points and successful interactions.
3. A focused comparison showing where alternatives make the same workflows easier.
4. A short, prioritized set of improvements, weighted toward usability and collaboration.

Current status (2026-11-01): Initial hands-on synthesis and primary-source Hex/Evidence product/growth research are complete and linked in [[Product Review Findings]]. Next work is empirical: validate the high-impact homelab findings, compare external-agent completion and review workflows, and extend to customer-grounded use cases. Record classic versus 4.0 beta in any Hex test. Final feedback has not yet been prepared or sent.
