# Evidence Studio: making agent-built reports easier to trust and maintain

**Hands-on product review · 1 November 2026**

## My assessment

Evidence helped me turn a broad goal and a connected database into a useful homelab dashboard. Its strongest moment was helping me decide **what was worth building**, not just generating charts I had already specified. Seeing components appear in preview, repairing errors through prepared prompts, and editing live with another account made the framework feel accessible.

The opportunity I see is to make the surrounding workflow as dependable as that build experience. At several transitions—database setup, diagnostic repair, reopening a conversation, and GitHub publication—I had to recover context or interpret product state myself. For a product that lets teams maintain reporting as code, those transitions are part of the value proposition.

**My central recommendation is to preserve Evidence's code-oriented foundation while making the agent a more continuous, state-aware interface to Studio.** I would start with work preservation, clear validation status, and understandable publication before committing to a larger interface redesign.

## What this review covers

I built Home Lab Analytics against Neon using the native Studio agent, compared a separate Claude/MCP build, tested invitation and live editing with a second account, and connected GitHub. The walkthrough took place on 31 October; subsequent research and reflection continued on 1 November. I combined dictated observations, supplied agent transcripts, one preserved publish screenshot, and current primary-source product/customer research.

This is one technical evaluator using two accounts, not a representative customer study. The Claude comparison was not a controlled model experiment. I did not run a hands-on Hex/Grafana comparison, measure query performance, or reproduce every reported failure. The homelab use case stresses freshness and trust; it does not establish that infrastructure monitoring should be Evidence's target market. Supporting records are identified by HLA numbers in the companion evidence note.

## Why I would consider Evidence over the alternatives

My strongest candidate answer is: **Evidence can make recurring reporting part of an existing software-maintenance workflow.** For a team reviewing data and software changes in GitHub, the potential value is keeping reports in that maintenance and release process, with an open-source runtime when deployment ownership matters.

The distinction needs to be specific. Evidence documents Studio/local authoring through an owned repository. Hex's classic Git export is a one-way YAML audit trail, with restrictions around review-enforcing branch protection. That matters to a team that wants its existing repository and PR process to govern reports. However, Hex already exposes analytical code and supports external-agent authoring; its new code-backed 4.0 is in private beta. An equivalent repository-driven report workflow for 4.0 remains unverified here. I would not claim that code access or agent compatibility belongs only to Evidence. [Evidence version control](https://docs.evidence.dev/features/version-control), [Hex Git export](https://learn.hex.tech/docs/explore-data/projects/git-export), [Hex MCP](https://learn.hex.tech/docs/api-integrations/mcp-server), [Hex 4.0](https://learn.hex.tech/docs/hex-4-0/what-is-hex-4-0)

Core's open-source runtime is another meaningful option for teams with deployment or ownership constraints. Self-hosting also brings operational responsibilities and does not include all Studio platform features. Studio's additional case is therefore the convenience of integrated authoring, collaboration, publishing, and reader services around that foundation—not simply access to the framework. [Self-hosting tradeoffs](https://docs.evidence.dev/self-host)

| Situation | What I would evaluate |
|---|---|
| Reports are revised, reviewed, and released alongside a data/codebase | Evidence's report files, framework, and repository workflow are a plausible fit. Demonstrate the second and third revision, not only the first build. |
| Analysts move between SQL/Python investigation and business-facing apps | Hex documents a broad analysis-to-app workspace. Evidence should make its own strengths legible rather than compete on every analytical feature. [Hex workflows](https://learn.hex.tech/tutorials/quickstart/hex-basics) |
| The primary job is infrastructure monitoring and alerting | Grafana is a natural comparator. It also supports Git-managed dashboards, so “as code” alone does not settle the choice. [Grafana alerting](https://grafana.com/docs/grafana/latest/alerting/), [Grafana Git Sync](https://grafana.com/docs/grafana/latest/as-code/observability-as-code/git-sync/provisioned-dashboards/) |
| A coding agent can build a custom dashboard | Test whether Evidence's components, validation, and conventions reduce later maintenance. A custom application can also have a repository; the comparison is the work the framework removes. |

Public customer evidence suggests useful next tests. Every Cure pairs knowledge-graph releases with Evidence quality/composition dashboards: reporting tied to a released data artifact. Brighthive describes agents using open-source Evidence to refine and share visualizations. These are relevant workflow examples, not proof of current Studio adoption or why those organizations chose Evidence over Hex. [Every Cure release](https://docs.dev.everycure.org/releases/2025/03/06/v040/), [Brighthive interview](https://www.brighthive.io/post/brighthive-your-ai-powered-data-team)

An illustrative job would be revising a quality report alongside a dataset release, reviewing the changes together, and retaining a report for that version. Every Cure makes the release-linked reporting need concrete; its actual Git/review process was not established by this research.

## Strengths I would preserve

- **Recommendations grounded in my data.** The agent connected my health-dashboard goal to useful components and missing telemetry. I liked the suggestions enough to add data sources. This reduced the burden of specifying every chart upfront. *(HLA-10–11)*
- **Visible progress.** Components appearing during generation made the build engaging and easier to follow. A future conversational interface should preserve that immediate connection to the artifact. *(HLA-12)*
- **A useful repair entry point.** Sending a diagnostic, line reference, and concise prepared prompt to chat saved effort. The shortcut itself worked well as an interaction idea; its effect on an active task needs improvement. *(HLA-15–16)*
- **Collaboration before Git setup.** My second account could sign up through an invitation, and edits appeared live in both sessions before I connected GitHub. That is concrete hosted-product value. *(HLA-37)*
- **Validation tools useful to external agents.** Claude used Evidence's query/render tools to iterate before handing over code, which I appreciated. That is a strength of Evidence's tooling; it does not establish that one underlying model is better. *(HLA-28, HLA-36)*

## Four opportunities I would prioritize

These are priorities for investigation and improvement based on this walkthrough. Customer-wide frequency and engineering effort are unknown, so I have not assigned numerical severity scores.

### 1. Preserve the task while helping me complete or repair it

During connection setup, I left the project to follow the agent's instructions. Consulting the agent again required returning to the project, and previously entered setup details were gone when I came back. Later, sending an error to chat interrupted a temperature-component request; it was not completed at that point. After reopening the main account, a recent conversation title remained visible but returned “chat not found.” These are distinct events with potentially different causes and a shared cost: rebuilding context or repeating work. *(HLA-01–02, HLA-16, HLA-38)*

**What I would try first:** reproduce and triage the chat-retrieval failure; preserve appropriate setup draft state; provide working navigation with contextual help; and queue a diagnostic repair or explicitly retain/resume the original request. A separate error agent is one option, not a prerequisite.

**Why it matters:** useful assistance loses value when invoking it displaces the work it supports. This is especially consequential if a conversation contains the reasoning behind a maintained report.

**Check the outcome:** can an author leave and return without re-entering work, reopen the conversation, and complete the original task after a repair? Track recovery and completed tasks, not just chat engagement. I have not established permanent deletion of any conversation.

### 2. Make “ready” mean something observable

I saw roughly five diagnostics while the agent was asking me to accept changes. In a separate temperature-format repair, warnings used the same generated “component error” wording, and the supplied agent response explicitly said it had not inspected the rendered section. The five diagnostics and later warnings were different episodes. *(HLA-13, HLA-18)*

**What I would try first:** use available diagnostics and rendering before completion language, and show a compact status: what changed, what was checked, and what remains unresolved. Preserve warning/error severity. An author should still be able to accept an imperfect draft knowingly; accepting an edit, validating a report, and publishing it are different checkpoints.

**Why it matters:** an integrated agent should reduce the effort of interpreting editor state. The Claude render/repair loop suggests useful tools already exist, although that does not establish how the native agent currently accesses them.

**Check the outcome:** introduce one known blocking error and one benign warning, then compare the completion message, diagnostics, and render. Measure repairs needed after a claim of readiness. Separately reproduce the Claude-recorded missing-temperature render before attributing a component defect; an unavailable reading must not silently become a healthy value. *(HLA-28, HLA-31, HLA-36)*

### 3. Make the mixed Studio/GitHub publish decision understandable

After connecting GitHub, Publish displayed a warning that remote changes would be overwritten. The captured dialog offered Cancel and Force Publish but did not show the affected changes within that dialog. I did not demonstrate an overwrite or lost commit. *(HLA-40; screenshot in evidence note)*

**What I would try first:** reproduce divergence in a disposable project, then examine whether an author can see the changes at risk, retain both working states, and take a clear review/reconciliation path. Make existing recovery options discoverable at the decision point.

**Why it matters:** supporting code-editor and Studio authors is attractive precisely because they can maintain the same reports. At this decision point, I could see that remote work was at risk, but not which changes I would replace. That made the next action harder to judge.

Evidence already documents PR checks/previews, publish history, and rollback. My recommendation is to make the relevant path understandable when it is needed, not to assume those capabilities are absent or prescribe a replacement Git implementation. [Publishing](https://docs.evidence.dev/publishing)

**Check the outcome:** have one person change a report externally while another has Studio work open. Can the Studio author explain what publication will replace, preserve the intended changes, and recover a known previous state?

### 4. Make the complete author-to-reader journey and data scope visible

After building reports, I still asked how a company would use them in meetings, where employees would open the agent, and whether connections belonged to projects. I also struggled to explain when I should choose Evidence over Hex. That is a real comprehension gap after initial success, rather than proof that the capabilities are missing. *(HLA-41–46)*

**What I would try first:** show a relevant example through connect → build → inspect → review → publish → reader question → later revision. Include the actual published-reader experience and a useful delivery path. Studio documents reader-facing AI, scheduled delivery, and embedding; I had not tested those workflows. [Evidence Agent](https://docs.evidence.dev/features/evidence-agent), [Scheduled reports](https://docs.evidence.dev/features/scheduled-reports), [Embedded analytics](https://docs.evidence.dev/features/embedded-analytics)

Make three questions legible: **what may I access, what should this investigation use, and what did the agent actually query?** I would like project-scoped connections, but central connections can reduce duplicated administration. Establish the intended boundary before prescribing a project-only architecture. No unrestricted agent access or security failure was demonstrated.

Pair the walkthrough with a customer story explaining the prior alternative, selection constraint, maintenance/delivery workflow, and outcome. My request is for clearer proof of fit, not a claim that Evidence has no customer stories.

**Check the outcome:** can a reader receive the published report, open it outside the editor, ask a relevant follow-up, and understand the sources behind the answer within their permitted access? Can the author identify the data boundaries and complete a later revision?

## A product direction I would test

I would explore **one continuing conversation with two views**:

- A chat view where I investigate selected data, see and organize generated artifacts, and inspect their logic.
- An IDE view exposing files, queries, components, and preview, with that same conversation alongside it.

Switching views should preserve the task and artifact state. Agent-assisted setup, connection, and team actions could extend the experience where appropriate to the user's role; the prototype should make actions and handoffs explicit rather than assume unrestricted automation.

This aligns with Evidence's stated direction: its Core announcement already describes agents working with inspectable, editable artifacts and people steering and validating them. My feedback is about carrying that direction consistently through Studio. [Evidence Core](https://evidence.dev/blog/evidence-core)

I would treat this as an interaction-design experiment, not a dependency for fixing the continuity problems above. Compare it with a smaller continuity improvement using the same tools and task: add a component, inspect SQL, repair an error, and deliver to a reader. A prominent chat can help exploration but also obscure source inspection; two views can add confusion if their state differs. Broader adoption is a hypothesis, not an established outcome.

The external-agent path deserves a separate decision. Claude could query/render through Studio MCP but could not save its page, so the handoff was code for me to paste into Studio. The documented tools currently match that boundary. If external authoring is a target workflow, a proposed page/diff landing in Studio's review flow could remove that handoff. If CLI/Git is the intended authoring route, make that route clear early. [Studio MCP](https://docs.evidence.dev/mcp/studio)

## Where I would take the investigation next

First, verify the retrieval, readiness, and divergent-publish cases above. Then test a customer-grounded recurring report with a technical author and a separate reader/reviewer. Change one shared metric, review the result, publish it, use it in a short decision meeting, and revise it again. This would test the maintained-report advantage more directly than another fresh dashboard build.

The questions I would bring to the team are:

1. Which customer segment most values Evidence's reporting/repository model, and what did they replace?
2. Where do successful Studio teams collaborate entirely in the browser, and where do they use Git/PRs?
3. What source, project, and permission boundaries should users expect in agent conversations?
4. Is the intended external-agent authoring path MCP, CLI/Git, or both?

My working answer to “why Evidence?” is **maintainable reporting built on a framework that people and agents can inspect and change, with Studio reducing the work of operating it together**. The build loop gave me reasons to believe that promise. Making the handoffs equally dependable would make it easier to choose—and to keep using.

---

Companion: [[Evidence Studio - Review Evidence]] contains the observation register, publish screenshot, research qualifications, and follow-up checks. Recommendations are based on the recorded experience; no new live-product changes or customer outreach were performed for this report.
