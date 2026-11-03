# Feedback package — editing decisions

Private working note. Updated 2026-11-02. This is outside the folder intended for Evidence.

## Agreed direction

- Build the package in stages, with Sam choosing what to include; do not fill the whole skeleton in one pass.
- Lead the summary with the agent making report writing as code approachable while keeping code and queries visible.
- Lead with the agent interfacing better with Studio workflows as well as task/conversation continuity. Clearer checking supports this main recommendation; it is not the lead priority. Introduce the main-chat/shared-IDE interface proposal only in the analysis. Explicitly recognize repair as an existing agent capability. Do not imply publishing caused a lost conversation or task; the actual examples are an interrupted request and an inaccessible earlier chat.
- Justify that continuity through less repeated work for maintainers and more time checking what readers will see.
- Ground customer reasoning in the data team and its business readers together. Sam's firsthand perspective remains that of a report author; reader benefits should be explained as reasoning, not invented reader tests.
- Aim for about **1,000 words in the main note**, retaining a brief entry for every walkthrough stage. Supporting detail is optional reading.
- The main note must be self-contained: a reader should understand what was built, what happened, and why it matters without opening another document. Supporting links at the end add depth and sources rather than missing explanations. Following the revision discussion, include one closing sentence on what was not tested, without a standalone limits section. Preserve precise qualifications beside individual uncertain claims.
- Keep the tone generally positive, natural, brief, and honest. Show where Sam got stuck, what surprised him, what he wanted, and his labeled reasoning about the experience.
- Keep competitor research out of the shared package; use it privately to sharpen the customer reasoning.

## Current stage

The revised main note leads with the verdict, customer lens, and three ordered themes before a shortened walkthrough. The companion analysis follows that theme order, the walkthrough records Sam's clarified outcome, and the AI-use note remains unchanged. References must retain a distinct MLA Works Cited bibliography as well as the research explanations, with matching inline MLA citations. No tables or claim IDs. Sam's latest changes retain compact formatting, descriptive links, simple section names, a one-sentence scope qualification, and a positive framework/runtime value thesis. Selected-source cleanup is complete: retain the ten sources supporting the chosen notes, with no unused reference placeholders. A final user reading pass remains.

## Reading and package choices

- Do not repeat the filename as an in-file title in the shared notes; Obsidian already displays it. Preserve Sam's removal of those headings.
- Keep the Good / Stuck / Surprised labels in the main walkthrough for skimming.
- Use the order: opening verdict, Who I Had in Mind, My Feedback, What I Did, then smaller wishes, the scope sentence, and AI use/supporting links. Retain the main section names What I Did and My Feedback. Use modest section headings and bold labels for individual stages/themes; attach descriptive links to the relevant text rather than repeated More detail / More reasoning blocks.
- Keep the research explanations in References as plain prose with inline MLA citations, followed by a separate Works Cited section containing all ten full bibliography entries. The merge must not replace the bibliography with annotations. The separate sources document stays deleted.
- The walkthrough companion should give a fuller, self-contained account of every stage, even where it repeats the main note. Its depth is optional, not required to understand the main note.
- Keep the separate AI-use note near 150 words: tools, roles, and what Sam decided or checked. Do not claim every generated explanation, metric, or product issue was independently verified.

## Analysis choices

- Rank the themes: (1) agent integration with Studio workflows and task/conversation continuity, (2) what changed and was checked, (3) lasting framework value. Include help carrying out connection and team setup within permissions, not just access to chat. Keep the shared chat/IDE idea as one possible larger direction; guided connection setup alongside the same agent, task retention during repair, and reliable chat reopening are the first improvements to explore. Do not claim engineering effort or a shared technical root cause was established.
- Include both project-scoped connections and a visible data choice for each investigation, framed as wishes/questions rather than unrestricted-access claims.
- Combine readiness and action history into one section: what changed, what was checked, what remains open, and what can be revisited.
- Current source check confirms the native agent already shows a diff and can modify project/page settings. Don't imply these are absent when discussing broader connection/team workflows.
- Include a brief copy-button and voice-input wish in the main note, with fuller personal reasons in the companion.
- Anchor customer reasoning in a data team maintaining guided account-health analysis for customer-success colleagues. Evidence's unnamed customer-health skill story is relevant source material; the specific roles and implications in the notes are Sam's interpretation, not disclosed customer facts or a tested scenario.
- Keep the untested possibilities of easier learning and shared repo understanding in the companion to leave room for the main argument.
- Keep the framework theme positive: BI components, shared definitions, validation, and familiar Git/IDE development practices are the value Sam sees. Do not force this section into a recommendation/test format or claim every developer uses Git. Describe the framework on its merits; do not call it a new programming language, criticize Python/YAML, or reintroduce competitors into the shared package.

## Revision decisions — 2 November 2026

Sam answered the questions raised by the external review and revision plan:

- **Main recommendation:** better agent interaction with Studio workflows alongside conversation/task continuity, with checking as an addition. This overrides the external plan's suggested checking-first order.
- **Outcome:** a dashboard Sam would keep using, and a promising first build needing more work. Do not claim it has become his primary dashboard or that every value was verified.
- **Overwrite warning:** keep it excluded from the entire shared package, including the screenshot. The private record remains.
- **Missing-temperature example:** drop it. No reproduction is part of this revision.
- **Structure:** accept feedback before the shortened walkthrough and one closing scope sentence. Retain all nine stages, including unresolved preview refresh, and Good / Stuck labels. The customer lens states the maintainer's job and explains what the personal homelab test can inform.
- **Argument:** the first two themes give an observed basis, a customer consequence, a useful first step, and an outcome check. Following Sam's clarification, the third theme is a positive assessment of the BI framework and its fit with familiar Git, local development, pull-request review, and IDE workflows. Remove the proposed second-report/definition-change test; do not present framework value as contingent on that test or claim to know what Evidence has tested internally.
- **Agent View:** Sam wants a conversation for exploring connected data, discussing reports and reusable workflows, helping set up the project and its skills, and viewing individual components. Users could ask follow-up questions about a component and add selected ones to a page, dashboard, or report. Explain the potential value to a data team; this is a proposal, not a tested customer outcome or a claim that existing conversational analytics is absent.
- **Terminology:** call Studio's existing files/code/preview layout the **IDE view**. The proposal is an Agent View sharing the conversation and task with that existing IDE view, not the addition of an IDE that Studio lacks.
- **Writing:** about 1,000 words, no competitor names in the shared package, no em dashes, descriptive links, and the existing MLA bibliography. Work from the selected observations; no new research source is needed for these changes.

The external documents are proposals. Their suggested reintroduction of excluded findings, optional team questions, fresh-agent checks, and additional product tests were not automatically adopted. The revision uses a self-contained reading check and mechanical link/content checks; no independent cold reader or live-product reproduction is implied.

## Walkthrough choices — latest round

- **Connecting data:** keep losing access to the agent as the lead. Re-entering form details is a small aside, not a major standalone finding; connect it to wondering whether the agent could handle setup with Sam. Also retain direct-versus-synced choice and difficulty finding documented navigation.
- **Fixing errors:** retain the helpful prepared repair prompt, the interrupted temperature request requiring another prompt, and accepting changes without clarity on what had been checked.
- **GitHub:** focus on recognition of the existing installation and the repository-selection workaround. Sam explicitly chose to leave the overwrite warning out of the entire shared package. Remove its screenshot and related mixed Studio/Git analysis placeholders from that folder; retain the private evidence/history. This is editorial selection, not retraction of the observation.
- **Building:** give the most space to data-grounded component suggestions and missing telemetry that Sam acted on. Mention visible queries and progressive preview briefly.
- **Teammate:** keep signup through the invitation and live editing positive, identified as Sam's second-account test. Latest steering removes role confusion from the entire shared package, including supporting details; retain it only in the private record.
- **MCP:** keep the appreciated render/check loop and manual code handoff. Leave agent-logged metadata/catalog and image-size problems out of the whole shared package, including supporting details. Do not claim the Claude page was pasted or published.
- **Data-scope questions:** analysis only; keep the returning-later walkthrough entry focused on the inaccessible conversation.
- **Navigation:** keep both the Docs-button expectation and the unresponsive Schedules Support button in the main note. The latter describes Sam's click, not a universal claim about support availability.
- **Preview:** retain the unresolved refresh question plainly; do not invent a test result.

The saved [[Product Feedback Planning]] copy also contains later clarifications that supersede older uncertainty: Sam accepted with diagnostics visible; the temperature work required another prompt; Force Publish was not checked by default and was used; the chat did not return. Do not ask these questions again or silently revert to the older report's limits. Sam chose to drop the Claude-only missing-temperature example and to keep a new reader test out of this package.

Working files: [[Studio Feedback Package/Evidence Studio Feedback]] and [[Product Feedback Planning]]. The earlier [[Evidence Studio - Product Review]] is background, not the chosen external format.
