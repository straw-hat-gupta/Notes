# Evidence product review plan

Created: 2026-10-31  
Source: Sam's dictated brainstorm and the organized review plan in this chat.

## Purpose and emphasis

**What makes Evidence a better way for a team to build, maintain, and share dashboards and reports—and how clearly does that value come through when using it?**

Focus primarily on usability, using collaboration as the main lens. Features matter when they help or prevent someone from completing a real task. Keep observed behavior, user expectations, hypotheses, and recommendations distinguishable.

Current hands-on walkthrough: [[Home Lab Analytics - Review Log]].

## Review questions

### Q1 — Why choose Evidence?

What value does Evidence provide over Hex, Grafana, or a dashboard built with an AI coding tool such as Claude?

Starting hypotheses from the brainstorm, not established product advantages:
- A standardized framework and reusable components reduce the work of building dashboards.
- A maintained collection of reports makes future dashboards and changes easier.
- Shared conventions make teammates' reports easier to understand and modify.
- Collaboration, publishing, or access management reduce work around the dashboard itself.

Refinement: an AI-built dashboard can also live in a maintained repository. Test what Evidence adds beyond storing code: reusable components, consistency, maintenance, collaboration, or another benefit.

### Q2 — Why choose Studio over open source?

What additional value does Evidence Studio provide compared with using the open-source framework?

- What work does Studio remove, and for whom: author, reviewer, administrator, or reader?
- Which parts of the workflow become easier, and is that benefit discoverable?
- Does Studio meaningfully improve collaboration?
- When would an open-source user have a clear reason to adopt Studio?

### Q3 — How well does collaboration work?

Follow a report through **create → share → review → revise → publish → maintain**.

- Can I share a dashboard with someone who needs to work on it?
- Can another person understand, reuse, and change what I built?
- How do teammates give feedback, coordinate changes, and recover from mistakes?
- Who can view, edit, publish, and manage access?
- How granular are permissions and roles across workspaces, individual reports, and underlying data?
- Before publishing, can I tell who will see the change?

### Q4 — How usable is the workflow?

Where do I feel frustrated, lose confidence, need help, or fail to complete the task?

- Can I discover the next action and understand what it will do?
- Does actual behavior match my expectation?
- When I need documentation, is it easy to find, relevant, and sufficient?
- Is an obstacle caused by discoverability, unclear behavior, a missing capability, or something still unknown?
- Which features or interactions make the workflow especially smooth?

A documentation visit is a signal to investigate, not automatically a defect. A missing feature can cause a usability problem; the categories can overlap.

### Q5 — Which customer use cases matter most?

Identify three high-value, recurring workflows among major Evidence customers and try them myself.

For each, establish:
- Who authors, collaborates, reads, and administers the result?
- What business outcome are they pursuing, and how often?
- Why did they choose Evidence, and what did they use before?
- What concrete result counts as successful completion?

Use customer conversations or available customer evidence. Do not assume these use cases are known yet. Home Lab Analytics is my exploratory walkthrough; whether it represents a major customer workflow remains unconfirmed.

### Q6 — Where do alternatives provide more value?

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

Current status: Home Lab Analytics walkthrough in progress. After setup friction, the agent reports generating `pages/homelab` using the direct Neon connector with one-minute auto-refresh. Sam accepted the staged page, clarified that it will be the primary health/status/load dashboard, and requested more component options. Sam liked the prioritized recommendations and reports adding the suggested data sources; which sources and whether ingestion is complete are not yet confirmed. The log preserves earlier setup issues alongside these positive observations. Agent technical claims, actual dashboard/refresh behavior, customer use cases, and competitor growth have not been independently verified as part of this note-taking session.
