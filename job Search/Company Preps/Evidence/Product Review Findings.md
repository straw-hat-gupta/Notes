# Evidence product review — working findings

Updated: **2026-11-01**. **Intermediate synthesis, not the final feedback to Evidence.**

**Edited report:** [[Evidence Studio - Product Review]] now provides the concise shareable argument, with [[Evidence Studio - Review Evidence|evidence and research notes]]. This document remains the collective working synthesis for future investigations; it should not be forwarded as the final report. No new live-product reproduction was performed during the report-writing pass.

This is the collective findings document for this review. Hands-on coverage is the Home Lab Analytics walkthrough: native Studio agent, Claude through MCP, two-account collaboration, and GitHub setup. Desk research now adds [[Hex vs Evidence - Product and Growth Research]]; it is not a hands-on Hex evaluation. Future use cases will extend these findings. Raw chronology and transcripts remain in [[Home Lab Analytics - Review Log]] (HLA-01–HLA-47); questions remain in [[Product Review Plan]].

**Evidence labels:** **Sam** = firsthand experience reported by Sam; **Screenshot** = inspected artifact; **Claude** = the external agent's logged technical observations, not independently reproduced here. Proposed explanations and improvements are analysis. Priorities below reflect potential impact in this walkthrough, not customer-wide frequency or validated severity.

## Current assessment

Evidence helped turn a broad request and connected data into an evolving dashboard. The most visible value was useful component suggestions, immediate preview, guided repairs, and shared editing. The strongest friction appeared around keeping context, validating output, and moving between setup, authoring, and publication.

**Working thesis:** The framework and authoring tools showed value; the experience of safely completing and maintaining the work was less consistent. This is supported within one personal use case, not a conclusion about the whole customer base.

**Central usability request — stronger agent integration with Studio:** “I do wish that Evidence was able to better interface with the rest of Studio functionalities and workflows.” In context, this concerns the agent's connection to the surrounding product. **Candidate feedback wording:** The agent helped me build the report; I want that assistance to carry through setup, navigation, debugging, validation, and publishing, with context preserved between steps and clear handoffs when I need to act. This connects F03–F05 and F08; publishing guidance and access clarity also relate to F01/F09. It is a request for a more coherent workflow, not evidence that every Studio action must be autonomous or that the agent currently lacks all these capabilities. [[Home Lab Analytics - Review Log#HLA-44 — Sam explicitly wants stronger agent integration with Studio workflows|HLA-44]]

**Concrete interaction proposal — one conversation, chat and IDE views (HLA-47):** Preserve proximity to source code and familiar codebase maintenance while making the agent a primary interface. Sam proposes:

- **Chat view:** A main conversation with visible generated reports, charts, and other outputs that can be inspected and organized.
- **IDE view:** Switch to a file-oriented editor with the same conversation in a sidebar, exposing source files and the work they define. Switching views preserves the conversation and task context.
- **Evidence framework throughout:** Generated work remains grounded in Evidence's components and reporting conventions, with access to the underlying code.
- **Studio actions through the agent:** Support warehouse/connection setup and team workflows as part of the conversation, within the user's permissions, with clear action outcomes and handoffs. This is a proposed integration scope, not a claim that Hex already automates these actions.

**Rationale to validate:** A technical audience can still prefer agent-led work; code-oriented maintenance and a primary chat interface can support the same person. Sam's belief that this reflects how developers now work motivates the proposal, but adoption and audience expansion have not been measured. This would connect the existing suggestions/preview benefits (P01/P02) to the continuity and handoff issues (F03–F05/F08). [[Home Lab Analytics - Review Log#HLA-47 — Code-oriented maintenance with one conversation across chat and IDE views|HLA-47]]

**Hex research update:** Compare complete workflows, not AI/MCP checkboxes. Hex documents in-product reviews and external-agent authoring; Evidence documents its open-source Core and own-repo workflow. Hex's new code-backed 4.0 is private beta, so “only Evidence is code-based” is not a defensible distinction. These are research-backed comparison questions, not observed Hex usability wins. Details, release caveats, sources, and growth hypotheses are in [[Hex vs Evidence - Product and Growth Research]].

**AI across the workflow — working comparison:** Hex appears to make AI a broader interface across the analytics lifecycle—from asking questions and investigating data to building apps and overseeing agent behavior. Evidence Studio also makes AI central to report creation and exploration; my testing so far raises questions about how smoothly its agent connects with the surrounding Studio workflow.

**Sam's interface distinction:** Hex feels like **a conversation that develops into inspectable analyses and reports**; Evidence has felt like **a report with an agent alongside it**. The desired interaction is to choose relevant data, investigate conversationally, inspect the generated logic, and turn useful results into a maintained report without losing context. This describes Sam's current impression, not exclusive capabilities: Evidence's native agent also built the homelab page from a broad request. [[Home Lab Analytics - Review Log#HLA-46 — Conversation-first analysis and visible data scope matter to Sam|HLA-46]]

**New usability requirement to test — visible analysis scope:** Sam wants an explicit way to focus an investigation on selected data instead of relying only on “don't use the other data” in a prompt. Distinguish **what the user may access**, **what this investigation should use**, and **what the agent actually queried**. “The agent has all data” remains unverified for Evidence. Hex's connection selector prioritizes a source but can switch to other permitted sources; its Governed mode guides source selection and explicitly is not a security boundary. A fair test must inspect source use and enforced permissions separately. [Hex Threads](https://learn.hex.tech/docs/explore-data/threads), [Governed mode](https://learn.hex.tech/docs/agent-management/governed-mode)

Hex's breadth is based on [[Hex vs Evidence - Product and Growth Research|documented capabilities]], not a hands-on comparison. The Studio integration concern is grounded in this walkthrough: repair interrupted the active request (F03), completion messages did not establish readiness (F04), and setup guidance lost continuity across pages (F05). This distinguishes breadth of AI capabilities from quality of integration; it does not establish that Hex works better in practice.

**Where the AI interfaces connect to work:**

| Workflow | Hex — documented | Evidence — documented and observed |
|---|---|---|
| **Investigate and build** | The Notebook Agent works within an analysis: it can create/edit SQL, Python, charts, and other cells using project context and warehouse schemas. The interface supports iterating on analytical logic as well as presenting results; technical users are expected to audit generated code. [Hex AI](https://learn.hex.tech/docs/getting-started/ai-overview) | In the homelab run, the project-side agent queried Neon, recommended components based on available data, and staged page edits for acceptance. Components appeared progressively in preview (P01/P02). The visible unit of work was an Evidence report page containing queries, components, and narrative. |
| **Ask questions as a reader** | Threads is a standalone conversational entry point for data questions. Chat with App connects questions to a published app: it can explain logic, change inputs/filters, and run the project. These question-asking interfaces require Explorer or higher; Chat with App also requires Can Explore access. [Hex AI](https://learn.hex.tech/docs/getting-started/ai-overview) | The Evidence Agent uses published reports, underlying SQL, and filter definitions to generate analytical answers under existing access controls. This supports the ongoing-question value Sam liked (P01), although answer accuracy as the data evolves remains untested. [Evidence Agent](https://docs.evidence.dev/features/evidence-agent) |
| **Supply context and improve behavior** | Context Studio gives Admins/Managers a management interface for guides, endorsed assets, semantic models, usage patterns, warnings, and evaluations. It connects questions being asked across the workspace to changes in the guidance agents use. Available on Team/Enterprise, with role-specific access. [Context Studio](https://learn.hex.tech/docs/agent-management/context-studio) | Version-controlled `agent/context/` files supply always-loaded instructions; `agent/skills/` holds analytical playbooks loaded on demand. Studio MCP exposes context and available skills to external assistants. This is also reusable AI guidance, organized through project files; an equivalent observability/evaluation interface has not been established in this review. [Evidence Agent](https://docs.evidence.dev/features/evidence-agent) |
| **Work from Claude or another external agent** | MCP supports workspace search and Threads, plus project/cell creation, editing, and execution. Knowledge tools require Explorer+; editing requires Editor+ and project permissions. MCP is beta on Team/Enterprise. This documents a route from external conversation to editable work inside Hex. [Hex MCP](https://learn.hex.tech/docs/api-integrations/mcp-server) | Studio MCP exposes reports, reusable source files, context, metadata, read-only SQL, and snippet rendering. Its current tool list has no page-save/publish action. In this run, Claude could render and repair its output, but Sam had to paste the code into Studio (P04/F08). Local file editing through a connected repo/CLI is a separate route, not a capability demonstrated by this MCP test. [Studio MCP](https://docs.evidence.dev/mcp/studio), [Version control](https://docs.evidence.dev/features/version-control) |
| **Review and publish generated work** | Hex has an in-product human review workflow with comments, approval, and requested changes on Team/Enterprise. This provides a place to review generated analysis before publication; it does not automatically verify correctness, and privileged users can override required reviews. [Reviews](https://learn.hex.tech/docs/collaborate/reviews) | Sam accepted staged native-agent changes, used shared editing, and then published through Studio. Git/PR review is available through the own-repo route, but the observed overwrite warning required a separate reconciliation decision (F01). Accepting an agent edit did not establish render readiness (F04); edit acceptance, validation, and publication are distinct checkpoints. |

**Release boundary:** Hex 4.0's private beta documents external-agent build → query/preview → publish, code-file-backed projects, and inspection of the logic/data behind app elements. It currently lacks Chat with App, scheduled runs, and other classic features. The table describes interfaces across Hex's product; it must not imply every interface is available together in a 4.0 project. [4.0 guide](https://learn.hex.tech/docs/hex-4-0/what-is-hex-4-0)

**Implication for the review:** Hex documents more explicit entry points for analysts, readers, and administrators. Evidence's native build loop already delivered value; the observed friction was at transitions between agent help and connector setup, between building and repair, and between external-agent output and a saved page. The comparative test should follow one request through **question → investigation → edit → validation → review/publication → reader follow-up**, recording context loss, manual handoffs, and permission boundaries. Neither platform's documented tool access proves seamless operation or authorizes agents to administer connections, invitations, or Git conflicts.

## What worked well

| ID | Finding and evidence | Why it matters |
|---|---|---|
| P01 | **Suggestions grounded in the data helped me decide what to build.** Sam liked the recommendations enough to add telemetry sources. [[Home Lab Analytics - Review Log#HLA-10 — Data-based suggestions are welcome; Sam accepts the staged page|HLA-10]] · [[Home Lab Analytics - Review Log#HLA-11 — Recommendations connect the primary-dashboard goal to components and missing telemetry|HLA-11]] | Reduces the need to specify every chart upfront. Ongoing questions about changing data are attractive, but their accuracy over time is still untested (HLA-35). |
| P02 | **Preview and prepared repair prompts reduced effort.** Sam enjoyed components appearing during generation and liked sending an error/line reference through a ready-made concise prompt. [[Home Lab Analytics - Review Log#HLA-12 — Components appear progressively in preview; Sam likes seeing the build happen|HLA-12]] · [[Home Lab Analytics - Review Log#HLA-15 — Diagnostic-to-chat action supplies a useful ready-made prompt|HLA-15]] | Makes progress visible and starts recovery without requiring prompt-writing expertise. Keep this benefit while addressing F03/F04. |
| P03 | **Inviting a new account and live co-editing worked.** Sam signed up a second account from an invitation and saw changes in both sessions before GitHub was connected. [[Home Lab Analytics - Review Log#HLA-37 — A new teammate can sign up from an invitation; Studio edits appear live in both sessions|HLA-37]] | Concrete collaboration value. This was Sam testing two accounts, not an independent novice maintenance test. |
| P04 | **Rendering before handoff improved the Claude workflow.** Claude logged actionable validation errors and render/fix iterations; Sam liked the checking and reported no errors in its page. [[Home Lab Analytics - Review Log#HLA-28 — `visualize` gives Claude a real render-and-fix loop with precise validation errors|HLA-28]] · [[Home Lab Analytics - Review Log#HLA-36 — Sam reports no errors in the Claude page and values validation before handoff|HLA-36]] | Evidence's own tools support a useful validation loop. Successful rendering does not establish correct interpretation of the data; see F07. |

## Pain points and candidate improvements

### F01 — Publishing asks the user to judge an overwrite risk

**Evidence — Screenshot + Sam:** After GitHub linking, Publish warned that remote changes would be overwritten. The captured dialog shows no affected-file comparison. [[Home Lab Analytics - Review Log#HLA-40 — Publish dialog warns that remote changes will be overwritten|HLA-40, screenshot and context]]

**Impact:** A maintainer must make a consequential Git decision to finish publishing. This directly challenges the mixed technical/nontechnical collaboration story.

**Direction:** Make the changes at risk understandable and guide reconciliation/review. **Limit:** No overwrite, lost commit, or failed recovery was demonstrated; the checkbox's default state is unknown. Highest-priority collaboration test before final feedback.

### F02 — A recent chat could not be reopened

**Evidence — Sam:** After closing and reopening the same main account, the conversation title remained in Recent but returned “chat not found.” [[Home Lab Analytics - Review Log#HLA-38 — Reopening the same main account leaves a recent chat inaccessible|HLA-38]]

**Impact:** Prior instructions and discussion became inaccessible, weakening the continuity of an agent-assisted workflow.

**Direction:** Investigate retrieval and recovery, including a useful failure state. **Limit:** Permanent deletion and reproducibility are unconfirmed; no report loss was reported.

### F03 — Repairing an error interrupted the requested work

**Evidence — Sam:** Sending a diagnostic to chat interrupted a temperature-component request, which was not completed at that point. [[Home Lab Analytics - Review Log#HLA-16 — Sending a diagnostic interrupts an existing component request|HLA-16]]

**Impact:** A helpful shortcut displaced the task it was meant to support.

**Direction:** Queue the repair, explain the interruption, or reliably resume the original task. A separate error-handling agent is one possible solution, not a demonstrated requirement. Later temperature edits do not prove automatic resumption.

### F04 — Completion messages did not establish that the page was ready

**Evidence — Sam + supplied agent output:** Sam saw approximately five diagnostics while being asked to accept changes. A later repair response explicitly said the rendered section had not been checked. Warnings were sent using the same “component error” prompt. [[Home Lab Analytics - Review Log#HLA-13 — Agent asks for acceptance while five errors remain visible|HLA-13]] · [[Home Lab Analytics - Review Log#HLA-18 — Warnings use the error prompt; agent reports a format fix without checking the render|HLA-18]]

**Impact:** The user carries the burden of reconciling the agent's confidence with the editor's state.

**Direction:** Inspect available diagnostics/rendered output before requesting acceptance and preserve diagnostic severity. The earlier five messages and later six temperature warnings are different evidence, not a proven unresolved single bug.

### F05 — Setup guidance lost continuity across pages and integrations

**Evidence — Sam:** Consulting the project agent required leaving connection setup; entered details were gone on return. A connector link did not navigate. GitHub repeatedly reported an existing installation until changing repository selection made it appear in Studio. [[Home Lab Analytics - Review Log#HLA-01 — Leaving the project separates setup from the agent; entered details are lost|HLA-01]] · [[Home Lab Analytics - Review Log#HLA-02 — A connector link exists, but clicking it does not navigate|HLA-02]] · [[Home Lab Analytics - Review Log#HLA-39 — Existing GitHub installation is not recognized until repository selection changes|HLA-39]]

**Impact:** Backtracking, re-entry, and trial-and-error during onboarding.

**Direction:** Keep help accessible, preserve drafts, and offer reliable connection-state recovery. These are related workflow problems, not a proven shared technical cause; the GitHub workaround is not a universal setup requirement.

### F06 — “Live” was difficult to reason about end to end

**Evidence — Sam + Claude:** Direct-versus-synced advice changed; Sam could not locate documented navigation and could not establish preview refresh behavior. Claude logged gaps in the Postgres documentation it read and different refresh units/minimums. [[Home Lab Analytics - Review Log#HLA-05 — Agent changes its recommendation; connector choice remains unclear|HLA-05]] · [[Home Lab Analytics - Review Log#HLA-14 — Preview versus published refresh behavior remains unclear|HLA-14]] · [[Home Lab Analytics - Review Log#HLA-26 — The direct Postgres connection is live, but the docs describe Postgres only as a synced source|HLA-26]] · [[Home Lab Analytics - Review Log#HLA-27 — The 1-second refresh setting is findable only by reading docs directly, and the documented limits conflict|HLA-27]]

**Impact:** It was unclear which setup met the primary-dashboard goal or how to verify freshness.

**Direction:** Give one coherent connector/refresh recipe, covering source cadence, queries, preview, and publishing. **Limit:** One-second behavior remains unmeasured; documentation observations describe what was retrieved during the run, not a fresh documentation audit. Rejecting `date_grain="minute"` had a plotting workaround (HLA-30), so minute-resolution charts were not shown to be impossible.

### F07 — Missing sensor data appeared healthy in a render

**Evidence — Claude:** A NULL temperature for an unsupported GPU sensor rendered as green **0 °C** in a heat grid. Claude worked around it by excluding missing readings and showing unsupported sensors separately. [[Home Lab Analytics - Review Log#HLA-31 — `heat_grid` shows a missing temperature as a green "0 °C"|HLA-31]]

**Impact:** Potential false reassurance on a health dashboard, even when syntax validation passes.

**Direction:** Distinguish unavailable readings from valid low values. **Limit:** High potential impact, but this is an agent-recorded render observation. Reproduce the minimal query/component and inspect aggregation/formatting before attributing the behavior to the component or presenting it as confirmed in the final review.

### F08 — The external-agent route had useful tools but an incomplete handoff

**Evidence — Claude; manual handoff confirmed by Sam:** Available MCP tools could query/render but not save the page. Catalog tools returned no tables while SQL found them. Render responses exceeded the client's size limit, and the full image omitted lower sections. [[Home Lab Analytics - Review Log#HLA-24 — Studio MCP is read-only: Claude cannot create `Home Lab_Claude.md`|HLA-24]] · [[Home Lab Analytics - Review Log#HLA-25 — `list_tables` and `get_metadata` return nothing, but SQL sees 26 telemetry objects|HLA-25]] · [[Home Lab Analytics - Review Log#HLA-29 — Render output is too large for the client, and long pages are cut off at 3200 px|HLA-29]]

**Impact:** SQL discovery fallbacks, image-processing steps, split renders, and code to paste into Studio.

**Direction:** Evaluate a reviewed page/diff handoff and clearer metadata/render contracts. Read-only authoring scope was documented; image-size friction spans MCP/client behavior. Neither proves that Studio itself lacks page creation or rendering.

### F09 — The reason to choose Evidence remains difficult to articulate

**Evidence — Sam's post-walkthrough impression:** After building the homelab dashboard and researching Hex, Sam still struggles to explain why choose Evidence. Hex appears to connect ideation, implementation, and delivery more clearly; Evidence's project sidebar feels less obviously connected to a broader agent experience. Sam hypothesizes different technical/nontechnical audiences and asks for customer stories showing Evidence's practical value. [[Home Lab Analytics - Review Log#HLA-42 — After the build and competitor research, the reason to choose Evidence remains unclear|HLA-42]]

**Impact:** Useful output and positive features have not yet produced a clear selection rationale. This is a positioning/discoverability finding from one evaluator, alongside the concrete workflow friction above.

**Qualification:** Evidence Agent is documented as part of Studio; Hex supports technical authors as well as business users. Sam's retraction is preserved in the raw log. Neither a missing conversational interface nor a strict “Hex = nontechnical / Evidence = technical” split is established. Public Evidence adoption examples already exist in [[Customer Use Case Research]], but those sources do not establish why customers chose Evidence over Hex or measured outcomes. [Evidence Agent](https://docs.evidence.dev/features/evidence-agent), [Hex AI](https://learn.hex.tech/docs/getting-started/ai-overview)

**Direction:** Explain the complete author/reader journey and make differentiated value tangible through relevant customer stories: **who had which problem → what they used before → why Evidence fit → how the team builds, maintains, and delivers the work → what improved**. Repo control, self-hosting, and reusable report components are candidate selection reasons to validate with buyers, not substitutes for demonstrated outcomes. Compare a technical maintainer and a less technical reader/reviewer separately.

**Follow-up evidence:** Sam also asks whether company users must interact through preview, where the published agent lives, and whether connections are assigned per project. This makes the author/reader and content/data boundary confusion concrete. Docs establish a published reader experience and organization-level data setup; per-project connection assignment remains unverified. [[Home Lab Analytics - Review Log#HLA-43 — Published reader experience and project/data boundaries are unclear|HLA-43]]

## Provisional answers to the review plan

### Q1 — Evidence's value

**Primary question for the remaining review:** What would make a specific team choose Evidence over Hex? Sam explicitly prioritizes this question in HLA-45. Candidate answers must connect a buyer constraint to a demonstrated outcome; more AI features or code files alone are insufficient. Prioritize testing ownership/deployment flexibility, report/definition reuse, and fit with an existing engineering workflow. These remain hypotheses, not established competitive wins.

**Sam's candidate answer (HLA-47):** Evidence keeps the report's source code central and lets a team maintain dashboards through familiar codebase workflows. The value to demonstrate is continuity with existing development, review, and maintenance practices. Hex also exposes code and supports external authoring, so test the practical depth of that workflow rather than claiming code access is exclusive to Evidence. The proposed chat/IDE experience would make this value accessible through an agent while preserving direct code control; it is a future direction, not an existing advantage.

**Partially answered.** P01/P04 support value in a structured reporting framework, reusable artifacts, and tools that help agents inspect data and produce useful output. [[Hex vs Evidence - Product and Growth Research]] adds a documented comparison of repository/deployment control versus a broader analytical workspace, with substantial overlap. A repo alone is not a differentiator—especially with Hex 4.0's code-backed direction. Long-term reuse and comparative task outcomes remain untested. Sam's continued difficulty explaining why choose Evidence is itself a positioning/discoverability finding (F09); clearer customer selection stories are needed alongside feature comparisons.

### Q2 — Studio's additional value

**Partially answered.** P02/P03 and F08 support integrated authoring, preview, accepting changes, and shared editing as concrete benefits. Claude's manual handoff makes the native authoring advantage visible; F03–F06 show integration gaps. No direct self-hosted/open-source comparison or willingness-to-pay test has been run. Do not assign every framework capability exclusively to Studio.

The research document now distinguishes current Core/Studio capabilities and published pricing; documented differences do not replace that missing hands-on comparison.

### Q3 — Collaboration

**Partially answered.** Invitation/signup and shared editing worked (P03). Understanding roles required explanation, and external Git publication raised an overwrite decision (F01/F05). Permission isolation, reviewer handoff, conflict recovery, and a novice completing maintenance remain untested. Live co-editing is positive evidence, not proof of the entire review/publish/maintain workflow. HLA-43 adds an explicit test of published reader/agent access and project-versus-connection scoping; page visibility must be distinguished from underlying data access.

**Connection-scope research:** Hex explicitly documents shared and project-only connections and separate query-authoring/result permissions. Evidence's per-project hosted connection scoping remains unverified; the pasted agent's assumption that every project can query the organization connection is not established. See [[Hex vs Evidence - Product and Growth Research#Connections, projects, and data access|connection comparison and permission test]]. This is a documentation distinction, not a tested security ranking.

**Sam's preference:** Scope connections per project (HLA-45). Exact sharing/reuse behavior is unspecified; this is a proposed product direction, not confirmation of a missing control. A more agent-centric Studio experience might broaden participation, but that audience hypothesis needs an independent less technical participant and a complete workflow test.

### Q4 — Usability

**Answered for this walkthrough; causes remain provisional.** The recurring costs were losing context/work, interpreting readiness, discovering the right setup, and validating freshness. Suggestions, preview, and repair prompts were helpful. F01–F08 provide concrete examples; they do not establish prevalence or severity across customers.

### Q5 — Priority customer use cases

**Open pending validation.** [[Customer Use Case Research]] provides three evidence-informed scenarios, not a ranking of the largest customers or a verified top-three workload. Home Lab Analytics is a personal exploratory case. Complete customer-grounded business/reporting workflows before calling these findings representative.

### Q6 — Alternatives and Hex growth

**Research comparison available; hands-on validation open.** [[Hex vs Evidence - Product and Growth Research]] compares product workflows, review/Git/MCP differences, pricing, and release boundaries, and separates Hex's published growth milestones from plausible contributors. It supports prioritizing external-agent completion and nontechnical review tests. It does not establish causal revenue drivers or empirical Hex superiority. The earlier Claude comparison still used Evidence on both paths. Grafana and standalone AI-built app comparisons remain open.

## What to investigate next

| Order | Investigation | Evidence needed to strengthen the review |
|---|---|---|
| 1 | F01: mixed Studio/GitHub edits in a disposable test project | Exact branch/diff, what the warning protects, reconciliation options, final content, and recovery. Avoid using the relied-on dashboard for a destructive test. |
| 2 | F07: missing/unsupported readings | Minimal synthetic NULL example and before/after renders; establish component versus query/format behavior. |
| 3 | F02–F04: resume, reopen, and repair | Reproduce reopening the same chat, sending a diagnostic mid-task, and requesting acceptance with known diagnostics. Record exact states and outcomes. |
| 4 | F06: freshness | Measure query reruns and source timestamps separately in preview/published views; check actual refresh limits and defaults. |
| 5 | Q3/Q5: another person and another customer workflow | Have a less technical participant maintain/review a report; test scoped roles and one scenario from the customer research. |
| 6 | Q1/Q2/Q6: fair comparison and ongoing reuse | Same data/task and explicit success criteria; inspect agent context/metric reuse and later changes. Then compare self-hosted Core and relevant alternatives. |
| 7 | Post-creation consumption | Use a report in a short review, export a dated PDF, test delivery, and investigate an authorized embed if available (HLA-41). |

## Items not to overstate in final feedback

- Voice input (HLA-22) and a response copy control (HLA-07) are smaller requests/discovery observations, not proven universal feature absences.
- Claude's swapped chart axes (HLA-32), collection cadence, collector labels, and chosen health thresholds (HLA-33) are not automatically Evidence defects.
- Claims about the native model's strength/training, permanent chat deletion, actual Git data loss, or unsupported one-second refresh are not established.
- Docs and agent explanations are context; observed behavior and reproductions should carry the final claims. Do not count repeated discussion as independent reproductions.

## Coverage and upkeep

| Investigation | State | Evidence |
|---|---|---|
| Home Lab Analytics: native + Claude/MCP + team/GitHub | Initial synthesis complete; targeted follow-ups open | HLA-01–HLA-47 |
| Customer-grounded business workflows | Proposed; not yet walked through | [[Customer Use Case Research]] |
| Meeting/distribution/embed journey | Question framed; not yet tested | HLA-41 |
| Hex vs Evidence product/growth research | Initial primary-source research complete; no comparative product runs | [[Hex vs Evidence - Product and Growth Research]] |
| Core/Hex/Grafana hands-on comparisons | Open; distinguish Hex classic from 4.0 beta | Q2/Q6 |

Keep this document thematic and short: add new evidence/use-case attribution to an existing finding when it changes confidence or scope; add a new finding only for a distinct important pattern. Keep raw observations in their case logs, mark resolutions, and update the six answers. Final feedback will be selected and refined from here after validation.
