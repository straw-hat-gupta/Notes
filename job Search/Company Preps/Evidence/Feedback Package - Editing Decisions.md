# Feedback package — editing decisions

Private working note. Updated 2026-11-03. This is outside the folder intended for Evidence.

## Agreed direction

- Build the package in stages, with Sam choosing what to include; do not fill the whole skeleton in one pass.
- Lead the summary with the agent making report writing as code approachable while keeping code and queries visible.
- Lead with the agent interfacing better with Studio workflows as well as task/conversation continuity. Clearer checking supports this main recommendation; it is not the lead priority. Introduce the main-chat/shared-IDE interface proposal only in the analysis. Explicitly recognize error fix as an existing agent capability. Do not imply publishing caused a lost conversation or task; the actual examples are an interrupted request and an inaccessible earlier chat.
- Justify that continuity through less repeated work for maintainers and more time checking what readers will see.
- Ground customer reasoning in the data team and its business readers together. Sam's firsthand perspective remains that of a report author; reader benefits should be explained as reasoning, not invented reader tests.
- Aim for about **1,000 words in the main note**, retaining a brief entry for every walkthrough stage. Supporting detail is optional reading.
- The main note must be self-contained: a reader should understand what was built, what happened, and why it matters without opening another document. Supporting links at the end add depth and sources rather than missing explanations. Omit the broad closing list of untested areas. Keep only qualifications needed to understand a specific claim, alongside that claim.
- Keep the tone generally positive, natural, brief, and honest. Show where Sam got stuck, what surprised him, what he wanted, and his labeled reasoning about the experience.
- Keep competitor research out of the shared package; use it privately to sharpen the customer reasoning.

## Current stage

The revised main note leads with the verdict, customer lens, and three ordered themes before a shortened walkthrough. The companion analysis follows that theme order, the walkthrough records Sam's clarified outcome, and the AI-use note remains unchanged. References must retain a distinct MLA Works Cited bibliography as well as the research explanations, with matching inline MLA citations. No tables or claim IDs. Sam's latest changes retain compact formatting, descriptive links, simple section names, claim-specific qualifications, and a positive framework/runtime value thesis. Selected-source cleanup is complete: retain the sources cited by the chosen notes, with no unused reference placeholders. A final user reading pass remains.

## Reading and package choices

- Do not repeat the filename as an in-file title in the shared notes; Obsidian already displays it. Preserve Sam's removal of those headings.
- Keep the Good / Stuck / Surprised labels in the main walkthrough for skimming.
- Use the order: opening verdict, Who I Had in Mind, My Feedback, What I Did, then smaller wishes and AI use/supporting links. Retain the main section names What I Did and My Feedback. Use modest section headings and bold labels for individual stages/themes; attach descriptive links to the relevant text rather than repeated More detail / More reasoning blocks.
- Keep the research explanations in References as plain prose with inline MLA citations, followed by a separate Works Cited section containing all thirteen full bibliography entries. The merge must not replace the bibliography with annotations. The separate sources document stays deleted.
- The walkthrough companion should give a fuller, self-contained account of every stage, even where it repeats the main note. Its depth is optional, not required to understand the main note.
- Keep the separate AI-use note near 150 words: tools, roles, and what Sam decided or checked. Do not claim every generated explanation, metric, or product issue was independently verified.

## Analysis choices

- Rank the themes: (1) agent integration with Studio workflows and task/conversation continuity, (2) what changed and was checked, (3) lasting framework value. Include help carrying out connection and team setup within permissions, not just access to chat. Keep the shared chat/IDE idea as one possible larger direction; guided connection setup alongside the same agent, task retention during error fix, and reliable chat reopening are the first improvements to explore. Do not claim engineering effort or a shared technical root cause was established.
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
- **Structure:** keep feedback before the shortened walkthrough; Sam later removed the broad closing scope sentence. Retain all nine stages, including unresolved preview refresh, and Good / Stuck labels. The customer lens states the maintainer's job and explains what the personal homelab test can inform.
- **Argument:** the first two themes give an observed basis, a customer consequence, a useful first step, and an outcome check. Following Sam's clarification, the third theme is a positive assessment of the BI framework and its fit with familiar Git, local development, pull-request review, and IDE workflows. Remove the proposed second-report/definition-change test; do not present framework value as contingent on that test or claim to know what Evidence has tested internally.
- **Agent View:** Sam wants a conversation for exploring connected data, discussing reports and reusable workflows, helping set up the project and its skills, and viewing individual components. Users could ask follow-up questions about a component and add selected ones to a page, dashboard, or report. Explain the potential value to a data team; this is a proposal, not a tested customer outcome or a claim that existing conversational analytics is absent.
- **Terminology:** call Studio's existing files/code/preview layout the **IDE view**. The proposal is an Agent View sharing the conversation and task with that existing IDE view, not the addition of an IDE that Studio lacks.
- **Writing:** about 1,000 words, no competitor names in the shared package, no em dashes, descriptive links, and the existing MLA bibliography. Work from the selected observations; no new research source is needed for these changes.

The external documents are proposals. Their suggested reintroduction of excluded findings, optional team questions, fresh-agent checks, and additional product tests were not automatically adopted. The revision uses a self-contained reading check and mechanical link/content checks; no independent cold reader or live-product reproduction is implied.

## Second review decisions

- Acknowledge the existing Analytics Agent in both the main note and analysis: questions, saved insights, insight content in reports, project context and skills, plus the Studio agent's documented authoring and settings capabilities. The proposed Agent View can be a more prominent view of the existing agent and an authoring experience alongside the IDE; these ideas can coexist.
- Frame the Agent View as a question. Keep both priorities: helping set up the project and its pages, skills, and other contents, and agent-centric development through conversational analysis, trying components, follow-up questions, and adding selected components to reports. Preserve one conversation across the Agent and existing IDE views.
- Credit the agent for settings changes and add the proper citation for version-controlled agent instructions. Attribute the render/check loop to Studio MCP's `visualize`; ask whether a similar check could run before Accept without claiming implementation cost or native tool access.
- Clarify the opening, add a brief connection between the positive framework theme and the first two themes, and keep qualifications beside the claims they affect. Retain the two previously excluded findings outside the shared package.
- Revise Obsidian first, then carry the agreed changes into the existing Google Docs while preserving any separate edits made there.

## Latest wording and reader observations

- Read the current Google Docs and all existing comments before editing; retain the document IDs, links, and comment threads. The revised Google Docs are the wording source for the Obsidian package so Sam's later edits carry across.
- Use “error fix” when referring to the agent fixing errors. Explain that connection setup was outside the project where chat was unavailable, that sending an error interrupted a temperature request, and that a listed Studio chat could not be reopened after closing and reopening Studio.
- Focus checking on the agent using diagnostics and inspecting the updated charts and tables before handoff. Do not ask for a completion note or unresolved-work summary. Write customer outcomes around what a user can do. For continuity, name completion time and repeated requests as possible measures; do not invent measured savings.
- Sam's homelab experience informs empathy with developers building, debugging, and revising projects over multiple sessions. Remove the abstract data-freshness bridge and the sentence dismissing that experience as evidence of customer needs.
- Sam liked the published chat's inline charts and tables, its full-page and small-popup layouts, and standalone insights that readers can refine, save as reports in their library, share, and return to. Do not imply the Analytics Agent cannot create standalone reports. Keep the authoring proposal focused on connecting this existing experience with project setup, pages, skills, and the IDE view.
- Remove the broad “What I didn't test” sentence, including its now-outdated statement that the published reader experience was not explored. Keep firsthand observations in Sam's voice and customer benefits and success criteria focused on users.

## Component inspection and Git workflow additions

- Add the component inspector as a positive in Theme 2, alongside the existing diff: selecting a component exposes Results and SQL for examining its data and query. Connect those manual inspection tools to the request for the agent to also check its own changes before handoff. Give the full experience in walkthrough Step 3 and explain its maintainer value in the analysis.
- Update main-note Step 8 with successful updates between GitHub and Studio plus the later pending-deletion observation. Keep the installation workaround and full test sequence in the walkthrough. The Studio branch used during that later test was not established; do not call it a failed feature-branch test or claim an actual overwrite happened.
- In the framework analysis, start with the documented recommendation of feature branches for teams, Commit for branch work, and the Studio Publish or GitHub PR release routes. Credit the documented PR checks and previews. Frame the shared-draft rationale as Sam's interpretation and the incoming-change/review workflow as his question.
- Add Version Control and Publishing to the MLA references, accessed 3 November 2026. The earlier overwrite-dialog screenshot and the new component screenshots remain outside the shared package; the screenshots supplied here are context only.

## Walkthrough choices — latest round

- **Connecting data:** keep losing access to the agent as the lead. Re-entering form details is a small aside, not a major standalone finding; connect it to wondering whether the agent could handle setup with Sam. Also retain direct-versus-synced choice and difficulty finding documented navigation.
- **Fixing errors:** retain the helpful prepared prompt for error fixes, the interrupted temperature request requiring another prompt, accepting changes with diagnostics visible, and the separate error fix whose rendered output was not inspected.
- **GitHub:** focus on recognition of the existing installation and the repository-selection workaround. Sam explicitly chose to leave the overwrite warning out of the entire shared package. Remove its screenshot and related mixed Studio/Git analysis placeholders from that folder; retain the private evidence/history. This is editorial selection, not retraction of the observation.
- **Building:** give the most space to data-grounded component suggestions and missing telemetry that Sam acted on. Mention visible queries and progressive preview briefly.
- **Teammate:** keep signup through the invitation and live editing positive, identified as Sam's second-account test. Latest steering removes role confusion from the entire shared package, including supporting details; retain it only in the private record.
- **MCP:** keep the appreciated render/check loop and manual code handoff. Leave agent-logged metadata/catalog and image-size problems out of the whole shared package, including supporting details. Do not claim the Claude page was pasted or published.
- **Data-scope questions:** analysis only; keep the returning-later walkthrough entry focused on the inaccessible conversation.
- **Navigation:** keep both the Docs-button expectation and the unresponsive Schedules Support button in the main note. The latter describes Sam's click, not a universal claim about support availability.
- **Preview:** retain the unresolved refresh question plainly; do not invent a test result.

The saved [[Product Feedback Planning]] copy also contains later clarifications that supersede older uncertainty: Sam accepted with diagnostics visible; the temperature work required another prompt; Force Publish was not checked by default and was used; the chat did not return. Do not ask these questions again or silently revert to the older report's limits. Sam chose to drop the Claude-only missing-temperature example and to keep a new reader test out of this package.

Working files: [[Studio Feedback Package/Evidence Studio Feedback]] and [[Product Feedback Planning]]. The earlier [[Evidence Studio - Product Review]] is background, not the chosen external format.

## Theme 2 revision: checking the report before handoff

- Keep Theme 2 and strengthen it around the agent using Studio's diagnostics and rendered output to check and fix its work before handoff. Preserve the live preview, diff, component Results/SQL inspector, and MCP render-and-fix loop as positives.
- Use “I'd expect the agent to check its own changes before handing them back for my review.” Sam remains responsible for reviewing the result; do not imply that the agent replaces that review or that Sam normally does not check the work.
- Remove the proposed completion note, “what remains open,” check-history requests, and related opening/bridge language throughout the shared package. The desired outcome is fewer errors reaching the user and fewer prompts needed to get a working result.
- Keep Theme 1 about workflow integration and task continuity; Theme 2 concerns checking the generated report. The unresolved preview-refresh observation remains in the walkthrough without a Theme 2 cross-reference.
- Update the main note, analysis, walkthrough, and reference explanations consistently. Preserve current Google Docs wording and comments before syncing Obsidian. No new Studio test was performed; the native agent's exact access to rendering tools remains unverified.

## Final audit decisions, 3 November 2026

- Sam confirmed personally refining an insight draft and saving it as its own report in the library. State those actions as firsthand experience in the main note, analysis, and walkthrough. Keep the Analytics Agent citation with its documented shareable insights, saved prompt/implementation notes, and reuse in maintained reports; References links the firsthand detail to the walkthrough.
- Keep the current level of detail and make light edits. Do not cut the Agent View proposal to meet the earlier approximate 1,000-word target.
- Correct Step 8's tag to Theme 3 and add the incoming-GitHub-change question to Theme 3's Git paragraph. Preserve the distinction between a pending-deletion observation and an actual overwrite.
- Define the chosen term “IDE view” once in the main note and analysis as files, code editor, and preview. This is the package's description of the existing layout.
- Use “customer-health” when describing McAskill's post; “account-health” remains Sam's own scenario. Use the documented “read the data behind charts and tables” for agent capability, keeping it distinct from inspecting a rendered image.
- Correct References so only the Rendering label is bold, format visualize as code in the main note and companions, and italicize Evidence Docs in the Studio MCP bibliography entry. Preserve all thirteen entries and the current native Google Docs links.
- Describe the feature-branch Publish behavior as the docs state it: a squash commit that overwrites published-branch changes. Do not infer that generic Git squash merging causes this behavior.
- Keep team setup as a future integration wish, not an observed failure. Keep “framework and runtime” as Sam's characterization and retain useful repetition across standalone companions. Keep the Support observation in the main note and the Docs observation in the walkthrough, matching the current Google Docs.
- Retain “error fix” while specifying that the temperature-format item was a warning. Replace the imperative on warning/error wording with a tentative improvement grounded in the prepared prompt.
- Clarify the AI-use note's reference to agent evals as built-in tests of agent behavior. No new product test, PDF export, or external delivery is part of this revision.
