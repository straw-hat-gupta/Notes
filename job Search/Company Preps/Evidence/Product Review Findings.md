# Evidence product review — working findings

Updated: **2026-11-01**. **Intermediate synthesis, not the final feedback to Evidence.**

This is the collective findings document for this review. Current coverage is the Home Lab Analytics walkthrough: native Studio agent, Claude through MCP, two-account collaboration, and GitHub setup. Future use cases will extend these findings. Raw chronology and transcripts remain in [[Home Lab Analytics - Review Log]] (HLA-01–HLA-41); questions remain in [[Product Review Plan]].

**Evidence labels:** **Sam** = firsthand experience reported by Sam; **Screenshot** = inspected artifact; **Claude** = the external agent's logged technical observations, not independently reproduced here. Proposed explanations and improvements are analysis. Priorities below reflect potential impact in this walkthrough, not customer-wide frequency or validated severity.

## Current assessment

Evidence helped turn a broad request and connected data into an evolving dashboard. The most visible value was useful component suggestions, immediate preview, guided repairs, and shared editing. The strongest friction appeared around keeping context, validating output, and moving between setup, authoring, and publication.

**Working thesis:** The framework and authoring tools showed value; the experience of safely completing and maintaining the work was less consistent. This is supported within one personal use case, not a conclusion about the whole customer base.

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

## Provisional answers to the review plan

### Q1 — Evidence's value

**Partially answered.** P01/P04 support value in a structured reporting framework, reusable artifacts, and tools that help agents inspect data and produce useful output. Sam also sees potential for ongoing questions about a report. A repo alone is not a differentiator, and long-term reuse, shared metric definitions, and superiority over a standalone AI-built app have not been demonstrated.

### Q2 — Studio's additional value

**Partially answered.** P02/P03 and F08 support integrated authoring, preview, accepting changes, and shared editing as concrete benefits. Claude's manual handoff makes the native authoring advantage visible; F03–F06 show integration gaps. No direct self-hosted/open-source comparison or willingness-to-pay test has been run. Do not assign every framework capability exclusively to Studio.

### Q3 — Collaboration

**Partially answered.** Invitation/signup and shared editing worked (P03). Understanding roles required explanation, and external Git publication raised an overwrite decision (F01/F05). Permission isolation, reviewer handoff, conflict recovery, and a novice completing maintenance remain untested. Live co-editing is positive evidence, not proof of the entire review/publish/maintain workflow.

### Q4 — Usability

**Answered for this walkthrough; causes remain provisional.** The recurring costs were losing context/work, interpreting readiness, discovering the right setup, and validating freshness. Suggestions, preview, and repair prompts were helpful. F01–F08 provide concrete examples; they do not establish prevalence or severity across customers.

### Q5 — Priority customer use cases

**Open pending validation.** [[Customer Use Case Research]] provides three evidence-informed scenarios, not a ranking of the largest customers or a verified top-three workload. Home Lab Analytics is a personal exploratory case. Complete customer-grounded business/reporting workflows before calling these findings representative.

### Q6 — Alternatives and Hex growth

**Partially answered for Claude/MCP only.** Claude's render/check process was appreciated, while native Studio avoided the manual code handoff. Both builds used Evidence, with different tools, context, timing, and data coverage. This does not establish that Claude is a stronger model or that generic AI coding replaces Evidence. Hex/Grafana comparisons and explanations of Hex's growth remain open.

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
| Home Lab Analytics: native + Claude/MCP + team/GitHub | Initial synthesis complete; targeted follow-ups open | HLA-01–HLA-41 |
| Customer-grounded business workflows | Proposed; not yet walked through | [[Customer Use Case Research]] |
| Meeting/distribution/embed journey | Question framed; not yet tested | HLA-41 |
| Core/Hex/Grafana comparisons | Open | Q2/Q6 |

Keep this document thematic and short: add new evidence/use-case attribution to an existing finding when it changes confidence or scope; add a new finding only for a distinct important pattern. Keep raw observations in their case logs, mark resolutions, and update the six answers. Final feedback will be selected and refined from here after validation.
