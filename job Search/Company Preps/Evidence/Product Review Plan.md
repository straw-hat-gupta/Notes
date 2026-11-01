# Evidence product review plan

Created: 2026-10-31  
Source: Sam's dictated brainstorm and the organized review plan in this chat.

## Purpose and emphasis

**What makes Evidence a better way for a team to build, maintain, and share dashboards and reports—and how clearly does that value come through when using it?**

Focus primarily on usability, using collaboration as the main lens. Features matter when they help or prevent someone from completing a real task. Keep observed behavior, user expectations, hypotheses, and recommendations distinguishable.

Current hands-on walkthrough: [[Home Lab Analytics - Review Log]].

AI workflow summary: [[How I Use AI]] — brief first-person account of how AI supports the review, kept current as the process develops.

Latest hands-on findings (2026-10-31): Sam reports successful invitation/signup and live co-editing with a second account, appreciates Claude's render/check-before-handoff workflow, and values asking ongoing questions about connected reports. New concerns are an inaccessible recent chat in the same account, GitHub installation recognition requiring a repository-selection workaround, and a Publish dialog explicitly warning of overwriting remote changes. The screenshot is preserved in the log (HLA-35–HLA-40). Mixed Studio/code-editor maintenance is now a priority collaboration test; no overwrite outcome has been verified.

External-agent comparison: [[Claude Dashboard Comparison Prompt]] — minimal user goals for an independent Claude/MCP build on `Home Lab_Claude.md`; setup and results tracked in the walkthrough log. Run completed 2026-10-31 (Claude Opus 5.5 in Claude Code): page built and render-checked, but not saved to Studio because the MCP is read-only — see [[Home Lab Analytics - Review Log#HLA-24 — Studio MCP is read-only: Claude cannot create `Home Lab_Claude.md`|HLA-24]] onward.

Customer research: [[Customer Use Case Research]] — public adoption evidence, edition caveats, three proposed customer-grounded walkthroughs, and questions to validate with Evidence. These are not a verified ranking of the largest customers.

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

Current status: Sam reports publishing and is now investigating GitHub version control, syncing, and maintenance by less technical collaborators. The review log includes a current documentation check separating managed-repo Studio collaboration, external GitHub workflows, and reader/editor roles; actual sync, invitations, and collaborator usability remain untested. Sam also requests voice-to-text in the Studio agent. Earlier findings about data-based suggestions, progressive preview, diagnostics, and task interruption remain recorded. Claude/MCP comparison setup is prepared, but no connection or run result has been reported. Customer research is in [[Customer Use Case Research]]. Technical claims and final dashboard behavior remain independently unverified. **Update 2026-10-31:** the Claude/MCP run has now happened. Claude connected through MCP and built an independent `Home Lab_Claude.md` (status banner, node grids, pipeline, temperatures, services, storage/network), checked each section with the MCP render tool, and saved it locally at `/Users/samgupta/evidence/claude-build/Home Lab_Claude.md`. It still has to be pasted into Studio, previewed, and published, because the MCP has no tool to save pages. Findings, by cause, are in the review log, HLA-24–HLA-34: under-documented direct Postgres and refresh limits (HLA-26, HLA-27); no minute time grain on line charts (HLA-30); a missing temperature shown as a green 0 °C (HLA-31); empty table-listing tools through MCP (HLA-25, likely the same as HLA-09); render-checking before handover as a positive (HLA-28). One-second refresh (`auto_refresh: 1000`) is still unverified in preview and on the published page.
