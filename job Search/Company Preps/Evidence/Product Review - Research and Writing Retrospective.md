# Product-review research and writing — process retrospective

Date: **2026-11-01**. Internal working note for a possible future skill; this is not a skill specification or part of the external product feedback.

Deliverables: [[Evidence Studio - Product Review]] and [[Evidence Studio - Review Evidence]]. Inputs: raw walkthrough, intermediary findings, review plan, customer research, competitive research, and original feedback-method notes.

## What we were trying to produce

A candid, useful review for Evidence that demonstrates product judgment: a clear value thesis, specific successful and frustrating interactions, proportionate recommendations, and honest limits. The hiring context should change the care of the writing, not cause either flattery or suppression of important evidence.

## Approach used

1. Read the existing plan and the user's feedback principles, then select claims from the raw log rather than forwarding the accumulated intermediary document.
2. Use three parallel agents for distinct challenges: evidence/provenance audit, current competitive/customer value research, and product-priority/design critique. These agents are analytical reviewers, not independent product-test participants.
3. Check primary documentation and customer-authored accounts, including current Core/Studio and Hex classic/4.0 boundaries. Inspect the preserved publish screenshot directly.
4. Frame each recommendation as observed trigger → consequence → smallest credible response → outcome check. Keep the chat/IDE design proposal separate from the demonstrated need for continuity.
5. Write a standalone main report and a separate evidence note; submit the draft back to the agents for adversarial review before finalizing.

## What worked

- **The raw log corrected the synthesis.** The native agent did recommend direct Postgres; a connector link existed but did not navigate; the five diagnostics and later six warnings were different episodes. Reading the original entry prevented stronger but inaccurate wording.
- **Independent challenge roles converged on a useful spine.** The build loop produced value; friction clustered at setup, repair, readiness, and shared maintenance. That is more useful than collecting every complaint or asking Evidence to become Hex.
- **Looking for counterevidence improved the review.** Evidence already declares an agent-oriented strategy and documents PR checks, publish history, and rollback. Hex exposes code; Grafana has Git Sync. These checks narrowed the differentiator to specific buyer/workflow constraints.
- **A real artifact anchored a consequential finding.** The screenshot supports a critique of the publish decision while ruling out claims of demonstrated overwrite, lost commits, or default checkbox behavior.
- **Primary customer examples made next tests less arbitrary.** Every Cure suggested release-linked quality reporting; Brighthive suggested conversational analysis handed into reusable reporting. Neither was relabeled a current Studio case or top-paying customer.
- **Splitting the deliverable protected readability.** The main report carries the argument and selected evidence; the companion retains confidence boundaries, secondary findings, and reproductions still needed.

## What did not work, or needed correction

- **Large batched document reads repeatedly truncated output.** Parallel work was useful, but sending entire long files through one response hid details. Targeted section/entry reads with bounded output were more reliable.
- **Canonical URLs mattered.** The competitive researcher reported `/self-host/index` failing while `/self-host` worked. A direct Brighthive fetch timed out; exact primary-domain search recovered relevant text. Do not convert a fetch failure into a product/source absence.
- **The intermediary had accumulated repetition and caveats.** It was useful for preserving thinking but unsuitable as the final report. Writing a new, shorter argument worked better than lightly polishing it.
- **Preference could drift into asserted product fact.** “Project-scoped connections would help me” must not become “Evidence exposes all data.” “Chat feels central in Hex” must not become “Evidence cannot build from a conversation.”
- **Feature presence was too coarse a comparison.** Git export, repo-driven editing, context sync, file inspection, independent runtime deployment, and code portability are different capabilities. They needed separate checks.

## Method principles worth retaining for a later skill

**Final draft-review corrections:** The evidence reviewer caught “I pasted the output,” which the log did not establish; the final wording describes code supplied for a manual handoff. It also changed “reconcile product state” to “interpret product state” because no Git reconciliation was demonstrated. The product reviewer removed a contrast that could imply Hex requires maintaining every report as a bespoke app, added a concrete hypothetical release-linked reporting job, and made reader delivery a behavioral success check. The competitive reviewer requested a separate Hex MCP citation and an explicit limit on applying classic Git-export behavior to 4.0. Final companion reviews found no remaining material evidence or product-scope issues. This is analytical review, not empirical validation.


- Keep a claim ledger with source type, exact observation, permissible inference, and missing verification.
- Separate user, artifact, agent, documentation, and hypothesis evidence; agents reading the same log do not multiply the sample size.
- Look for contrary facts before recommending a missing feature. Ask whether existing capabilities are undiscoverable, disconnected, or actually absent.
- Tie priorities to task impact and strategic fit. Do not invent frequency, implementation effort, severity scores, or business ROI from one evaluator.
- Give design ideas at least one smaller competing solution and an assumption test. Broader agent autonomy is not automatically the right answer to continuity problems.
- Protect what worked, including positive behaviors that caused the user to take action.
- Describe the buyer constraint and recurring workflow before claiming competitive advantage. Treat pricing, growth, and customer logos as leads rather than proof of product causality.
- Keep process notes and job-search strategy out of the external report.

Method sources consulted: [NN/G severity guidance](https://www.nngroup.com/articles/how-to-rate-the-severity-of-usability-problems/) and [Teresa Torres on discovering solutions](https://www.producttalk.org/discovering-solutions/). Frequency/impact/persistence and opportunity/solution separation were applied to the actual findings rather than included as generic framework sections.

## Boundaries of this run

This work produced a written synthesis and refreshed desk research. It did not reproduce the Studio failures, test Hex/Grafana, measure maintenance outcomes, contact customers, change infrastructure, or submit feedback externally. A later skill should include optional empirical checks when access, time, and authorization support them; the current report does not claim those checks occurred.

No skill was created. Keep this note updated with any material final-review corrections and future lessons from delivering or testing the report.
