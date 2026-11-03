# Third review of "Evidence Studio Feedback" (final pre-send audit)

Reviewed 2026-11-03. Read only: no package or context file was changed. Live Evidence pages were fetched on 2026-11-03 through WebFetch (summaries of the live pages; quotes below come from those summaries).

## 1. Verdict

**READY AFTER MUST-FIXES.** The package now meets Sam's bar on structure, tone, self-containment and the no-Hex rule, and every audit 2 P0 is fixed. Four small things should be fixed before sending: one visibly broken bold paragraph in References, one walkthrough theme tag that points to a theme that does not discuss it, a citation that credits the Analytics Agent page with details it does not contain, and the "account-health" label applied to Adam McAskill's own "customer-health" post. All four are wording-level fixes of a few minutes each.

## 2. Must-fix before sending

**M1. References.md: the whole "Rendering" paragraph is bold (formatting artifact).**
- Current text (line 11): `**Rendering. Studio MCP documents visualize for rendering Evidence components and Markdown. Claude used it to check its page during my separate build; I did not establish how the native Studio agent accesses that tool (**[**"Studio MCP"**](https://docs.evidence.dev/mcp/studio)**).**`
- Every other paragraph bolds only its label. This one renders as a fully bold paragraph with a bold link, which looks like a paste error (probably from the Google Docs round trip).
- Replace with: `**Rendering.** Studio MCP documents `visualize` for rendering Evidence components and Markdown. Claude used it to check its page during my separate build; I did not establish how the native Studio agent accesses that tool (["Studio MCP"](https://docs.evidence.dev/mcp/studio)).`

**M2. Evidence Studio Feedback.md, Step 8: "(Theme 1)" points to a theme that never mentions GitHub.**
- Current text: "**Stuck:** With unpublished Studio edits present, a later GitHub addition appeared as a pending deletion in Studio (Theme 1)."
- Theme 1 is about the agent carrying setup, error fixes and chats. Nothing in it covers Git or pending changes. The only place this observation is discussed is the companion's framework section ("How should a Studio author bring those incoming changes into the draft..."), which corresponds to Theme 3. A reader who follows the tag finds nothing.
- Fix options: (a) change the tag to "(Theme 3)" and add one clause to Theme 3's Git paragraph, e.g. "The one place I got unsure was bringing a newer GitHub commit into an unpublished Studio draft (step 8)."; or (b) drop the tag. Option (a) is better because it gives Theme 3 its only observed friction and makes the walkthrough back the argument.

**M3. Analytics Agent citation covers details the cited page does not contain.**
- Main note, Theme 1 paragraph 3: "Insights can be refined and saved as standalone reports. I particularly like this because readers can keep and share useful analysis about a report and return to it later (["Analytics Agent"](https://evidence.dev/product/analytics-agent))."
- Analysis line 21: "...show charts and tables in chat, and build standalone insights... Users can refine an insight draft and save it as its own report in their library... (["Analytics Agent"]...; ["Evidence Agent"]...)."
- References line 9: "builds shareable insights that can be saved as standalone reports".
- What the page says (checked 2026-11-03): "Anyone on your team can ask a question and save the answer as an insight they can share", prompt and implementation notes are stored with the insight, and you can "lift the work out of an insight and into the reports and dashboards your team maintains". The words "refine", "library", "standalone" and "table" do not appear, and full-page vs popup chat is not described. The Evidence Agent docs page does not cover these either. These details come from Sam's own use of the published project (recorded only in Editing Decisions: "Sam liked the published chat's inline charts and tables, its full-page and small-popup layouts, and standalone insights that readers can refine, save as reports in their library").
- Why it matters: Sam's rule is that claims are traceable, and the readers wrote that page. The fix is to mark these as firsthand and keep the citation for what the page says.
- Suggested main-note wording: "In my session I could refine an insight and save it as its own report. I particularly like this because readers can keep and share useful analysis about a report and return to it later. Evidence describes saving answers as shareable insights and lifting insight work into maintained reports (["Analytics Agent"](...))." Make the matching change in Analysis line 21 ("In the published project I could also refine an insight draft and save it as its own report in my library") and References line 9.

**M4. "Account-health" is attributed to Adam's post, which says "customer-health".**
- Main note line 9: "Evidence's account-health skill story informed that scenario".
- References line 15: "Evidence describes an unnamed customer turning a complex account-health dashboard into a guided skill".
- The post (McAskill, 7 Aug 2026): "One of our customers recently refactored their customer-health dashboard into a skill." Adam is one of the interviewers and wrote this post. Using "account-health" for Sam's own scenario is fine; describing his post with it is a small misquote. (Audit 2 P2-1; not addressed and no decision recorded. Editing Decisions itself says "Evidence's unnamed customer-health skill story".) Analysis line 7 already avoids the problem ("a complex health dashboard").
- Fix: main note "Evidence's customer-health skill story informed that scenario"; References "a complex customer-health dashboard".

## 3. Should-fix (worth doing, not blocking)

**S1. "IDE view" is never defined in the main note and is not Evidence's term.** First use: "an Agent View alongside Studio's existing IDE view". The Editing docs call the panes "Code Editor" and "Preview" and never say "IDE view". The term is Sam's documented choice (Editing Decisions: "call Studio's existing files/code/preview layout the IDE view"), so keep it, but gloss it once: "Studio's existing IDE view (files, code editor, and preview)".

**S2. "What I built" line.** "A live homelab health dashboard with Neon db, using Studio's agent, with a separate Claude/MCP build, a second-account collaboration test, and GitHub setup." "Neon db" is informal (the walkthrough says "Neon Postgres") and the sentence stacks "with ... using ... with". Suggest: "A live homelab health dashboard on my Neon Postgres data, built with Studio's agent, plus a separate build with Claude over Studio MCP, a second-account collaboration test, and a GitHub connection."

**S3. Version Control wording.** Analysis line 57: "explicitly warns that the Studio Publish path can overwrite published-branch changes"; References line 17: "The docs warn that the Studio Publish path can overwrite published-branch changes". The page has no warning block; its Studio route says Publish "creates a squash commit, and will overwrite any changes on the published branch." Suggest: "notes that Studio Publish creates a squash commit and will overwrite any changes on the published branch".

**S4. Analysis line 21: "the Studio agent can query connected data, inspect visualizations, and edit pages and settings".** The docs say the agent can "Pull the data behind a chart, table, or value already on the page". "Inspect visualizations" reads as visual inspection, which slightly undercuts Theme 2's wish that the agent inspect rendered output. Line 39 already has the precise version ("read visualization data"). Suggest "read the data behind charts and tables".

**S5. Analysis line 45 is the one imperative left:** "Keep warnings and errors distinct so a warning is not presented as a blocking error." Sam's rule is observations and hypotheses, not prescriptions. Suggest: "It might also help to keep warnings and errors distinct, since the prepared prompt called a warning a component error."

**S6. Works Cited italics.** `"Studio MCP." Evidence Docs, [...]` is the only entry without `*Evidence Docs*`.

**S7. Main note length.** About 1,245 words (wc -w), against Sam's ~1,000 target (audit 2 measured ~1,040). Theme 1 is now four paragraphs (~430 words). If trimming, paragraph 4 ("Could an Agent View build on this...") overlaps heavily with Analysis "My question"; it could be cut to two sentences. Not blocking: it reads fine.

**S8. Delivery format check.** All internal links are relative `.md` paths with `%20` and heading anchors (for example `Walkthrough%20Details.md#2.%20Connecting%20my%20database`). They resolve in Obsidian (26 of 26). Editing Decisions says the Google Docs are now the wording source. If the package is sent as Google Docs or PDF, these links will not work; re-link in the delivery format, and make sure the Google Docs carry M1 to M4.

## 4. Optional polish

- Name the tool in the main note, since Evidence built it: "the loop Claude followed through Studio MCP's `visualize` tool". In Analysis line 39 and References line 11, format it as `visualize`. (Audit 2 P1-2 was addressed in the companions; the main note credits Studio MCP generally.)
- Theme 3: "a framework and runtime focused on BI" is cited to the Core post, which calls Core an "open-source framework for building data apps as code" and does not use "runtime". Fine as Sam's characterization; "framework" alone would be exact.
- The temperature-format item was a warning (the agent: "It's a warning, not an error"); the main note calls it "a separate temperature-format error fix". Sam deliberately uses "error fix"; the walkthrough is accurate. Leave unless you want precision.
- Quote style is mixed: curly in “That Dashboard”, “Evidence Core”, “chat not found” and one curly apostrophe ("An agent that’s integrated"), straight elsewhere (["Editing"]).
- Repetition across docs: "promising first dashboard I'd keep using and develop further" appears in the main note, Walkthrough and Analysis; "put myself in the customer's shoes" appears in the main note and twice in Analysis (lines 5 and 11).
- How I Used AI: "An early suggestion that Evidence had evals was corrected" may puzzle a cold reader (what evals?). True per HLA-48. Could add "(that Evidence ships agent evals)".
- Theme 1 wishes for help with "team setup", but the main note records no team-setup friction (Step 7 is Good; role confusion was removed by Sam). Harmless, but "connection setup" alone would match the evidence.
- Editing Decisions says to keep both the Docs-button and Support-button observations in the main note; only Support remains. Fine either way.

## 5. Prior findings status

### Audit 1

| # | Finding | Status | Current text / where decided |
|---|---|---|---|
| 1 | No spine | Addressed | "My main wish is for the agent to work more directly with Studio's workflows, carrying the conversation and task through setup, error fixes, and return visits." |
| 2 | Proportions; walkthrough first | Addressed | My Feedback precedes What I Did; Stuck lines carry theme tags (but see M2). |
| 3 | Homelab bridge | Addressed | "My homelab dashboard is a monitoring use case... What carries over is the developer experience of building, debugging, and revising a project over multiple sessions." |
| 4 | Value thesis, job line, second-report test | Addressed / test declined | Job line: "keeping an account-health assessment correct as data and methods change". Test removed by decision (Editing Decisions: "Remove the proposed second-report/definition-change test"). Theme 3 now ties back. |
| 5 | Recommendations stop at "I'd like" | Addressed | "I'd start with...", "I'd judge the improvement by...", "The improvement I'd look for is fewer errors reaching the user..." |
| 6 | Did it work? | Addressed | "I ended with a promising first dashboard I'd keep using and develop further." |
| 7 | Caveat density; "what I didn't test" line | Caveats trimmed; line intentionally declined | Editing Decisions: "Remove the broad 'What I didn't test' sentence". |
| 8 | Overwrite warning, green 0 °C | Intentionally declined | Editing Decisions: "Overwrite warning: keep it excluded"; "Missing-temperature example: drop it." Screenshot not referenced anywhere in the package (checked). |
| 9a | Data scope weakest | Addressed | One question under Smaller wishes. |
| 9b | Copy/voice space | Addressed | One clause. |
| 9c | Reader side missing | Addressed differently | Sam explored the published chat and insights (Theme 1 paragraph 3; Walkthrough "Published chat and insights"). |
| 9d | Questions for the team | Partly (by decision) | Framed as questions in Themes 1 and 2 ("Could an Agent View...", "Could the Studio agent follow a similar loop..."). Separate team questions declined (Editing Decisions: "optional team questions... were not automatically adopted"). |
| 9e | Typos ("a the", double space) | Addressed | Neither present. |

### Audit 2 (and the memory summary)

| # | Finding | Status | Current text / note |
|---|---|---|---|
| P0-1 | "it'd like to know" | Addressed | Sentence rewritten; no "it'd" in package. |
| P0-2 | Settings attributed to editor | Addressed (all three docs) | Main: "The agent can already adjust project and page settings"; Analysis line 19; References "The agent already shows a diff and can adjust project/page settings". Verified against Editing docs: "Adjust project and page settings (theme, layout, ...)". |
| P1-1 | Acknowledge Analytics Agent; Agent View as question | Addressed | Theme 1 paragraphs 3 and 4; "Could an Agent View build on this...". New citation issue in M3. |
| P1-2 | Credit Studio MCP `visualize` | Partly | Main note credits "the loop Claude followed through Studio MCP"; Analysis and References name `visualize`. Tool name verified on docs.evidence.dev/mcp/studio. See Optional. |
| P1-3 | Restore "what I didn't test" | Intentionally declined | Editing Decisions, "Latest wording": "Remove the broad 'What I didn't test' sentence". |
| P1-4 | Tie Theme 3 to Themes 1 and 2 | Addressed | "That's why I want the agent to stay connected to the task and check its work before handoff: it helps people build on that foundation with confidence." |
| P1-5 | Vague friction phrase | Addressed | "The friction came during database setup, when an error fix interrupted my request, and when I couldn't reopen a previous Studio chat." |
| P2-1 | customer-health vs account-health | Not addressed, no decision recorded | Now M4 (limited to the two places that describe the post). |
| P2-2 | Add Evidence Agent citation in Theme 3 | Addressed | "(["Evidence Agent"](...); ["CLI"](...))". |
| P2-3 | Theme tags | Partly | Step 6 fixed ("Render/check loop (Theme 2)... manual handoff (Theme 1)"). Step 8 now tagged, but with the wrong theme (M2). |
| P2-4 | En-dash ranges | Addressed | Zero en dashes; "Themes 1 and 2", "29 to 31 October 2026". |
| P2-5 | Delivery format / title | Title declined (Editing Decisions: "Do not repeat the filename as an in-file title"); links still Obsidian-style | See S8. |
| P2-6 | "experince" run-on | Addressed | "In my experience it is faster than typing and lets me express my thoughts more naturally." |
| P2-7 | Steps vs stages | Addressed | "walkthrough steps 2, 4, and 9". |
| P2-8 | Postgres-only-synced docs detail | Not adopted | Optional and Claude-sourced; fine to leave out. |

### Revision plan

| Item | Status |
|---|---|
| D1 checking first | Declined (Sam: continuity first, checking as addition) |
| D2 / D3 overwrite warning, 0 °C | Declined |
| Step 1 spine (job, pattern, recommendation, did it work) | Done |
| Step 2 A to E structure | Done, except E's questions and scope sentence (declined) and "Bugs I hit" (reduced to one Navigation line) |
| Stage 5 removed | Declined; kept as an honest one-line open question |
| Step 3 caveats to about 6 | Roughly met in the main note |
| Step 4 companions updated | Done; Analysis follows theme order |
| Step 5a independent cold read | Not done by an independent reader (Editing Decisions says so); Section 10 below is my cold read |
| Step 5c word count ~1,000 | Over: ~1,245 (S7) |

## 6. Fact-check: main note

| Claim | Support | Status |
|---|---|---|
| Time spent 1.5 to 2 h building, 3 to 4 h research | None in notes | Unverifiable self-report; fine |
| Live homelab dashboard on Neon, Studio agent, Claude/MCP build, second account, GitHub | Log context section; HLA-24, 37, 39 | Supported |
| "promising first dashboard I'd keep using" | Editing Decisions ("a dashboard Sam would keep using, and a promising first build") | Supported (Sam's statement) |
| Suggestions came from my data; could follow Markdown, SQL, preview | HLA-10, 11, 12 | Supported |
| McAskill post: unnamed customer's health dashboard turned into a skill | evidence.dev/blog/that-dashboard-should-be-a-skill (7 Aug 2026): "refactored their customer-health dashboard into a skill" | Verified; term mismatch (M4) |
| Connecting Neon took me outside the project; no agent chat there | HLA-01 | Supported |
| Sending an error to chat interrupted the temperature request; had to ask again | HLA-16 + Editing Decisions clarification | Supported |
| Listed chat returned "chat not found" after closing and reopening | HLA-38 | Supported |
| Agent can adjust project and page settings | docs.evidence.dev/editing: "Adjust project and page settings (theme, layout, table of contents, default date range, and more)" | Verified |
| Published chat shows charts and tables; full-page or small popup | Editing Decisions (Sam's report); not on cited page | Firsthand, not in raw log (M3) |
| Insights can be refined and saved as standalone reports | Sam's report; Analytics Agent page says "save the answer as an insight they can share" and "lift the work out of an insight and into the reports" | Partly verified; refine/standalone not on page (M3) |
| Live preview and component inspector (Results and SQL) | Editing Decisions ("selecting a component exposes Results and SQL"), screenshots not in package | Sam's report; not in raw log |
| Diff helped me understand what changed | Product Feedback Planning: "the agent does show the diff whenever it makes changes"; Editing docs "diff view" | Supported (product fact verified; usefulness is Sam's) |
| Accepted with about five errors visible | HLA-13 + Editing Decisions ("Sam accepted with diagnostics visible") | Supported |
| Temperature-format fix; agent hadn't inspected rendered section | HLA-18: "I haven't looked at the rendered temperature section since this change." | Supported (item was technically a warning) |
| Claude rendered, used validation feedback to fix, checked before handoff | HLA-28 (Claude-recorded), HLA-36 (Sam: "able to render and check everything before giving it to me") | Supported |
| Studio MCP link / tool | docs.evidence.dev/mcp/studio lists `visualize`: "Render an Evidence Markdoc snippet to an image" | Verified |
| Core: framework focused on BI with queries, reusable metrics, components, validation | evidence.dev/blog/evidence-core (26 Aug 2026): "connects directly to your data warehouse", "standalone metrics that can be reused", static validation | Verified ("runtime" not in post) |
| Agent instructions in Git; local editing; PR review | Evidence Agent docs: "version-controlled files that ship through the same git workflow as your pages"; CLI: "Develop... with the agent of your choice", PR "preview link" | Verified |
| Step 2: agent corrected advice, recommended direct connection | HLA-04, 05, 08, 09 | Supported |
| Step 5: one-second refresh in preview unresolved | HLA-14 | Supported |
| Step 6: code needed manual handoff | HLA-24, HLA-36; MCP docs "query data and read published reports" | Supported |
| Step 7: second account signed up via invite; live edits | HLA-37 | Supported |
| Step 8: GitHub commits appeared in Studio and Studio publishes on GitHub; later GitHub addition shown as pending deletion | Editing Decisions only ("successful updates between GitHub and Studio plus the later pending-deletion observation") | Sam's report; not in raw log |
| Navigation: Support button on Schedules did nothing | Product Feedback Notes (29 Oct) | Supported |
| Copy button, voice input wishes | HLA-07, HLA-22 | Supported |
| AI use line | Private How I Use AI.md | Consistent |

Companion spot checks: Components ("Typed" attributes; invalid values underlined) verified; Metrics ("The definition owns the aggregation SQL, filter, fmt, and label; components inherit them") verified; CLI connections ("use the connection, credentials, and access rules your organization has already set up") verified; Row Level Security (table access, RLS, "To use access rules with a Direct Connector, refer to that connector's documentation") verified; Version Control (main-only for solo, feature branches for teams, shared working state, commit button, Publish vs PR) verified, wording issue S3; Publishing (Markdown and access.yaml validation, preview comment, merge publishes) verified; Walkthrough dates "29 to 31 October 2026" supported (29 Oct notes, 31 Oct log); How I Used AI evals line supported by HLA-48.

## 7. Link check

- Internal Markdown links: 26 found across the five files; all 26 target files exist in the package and every `#heading` anchor exactly matches a heading in the target (script below). No link points to a private context note.
- Wikilinks `[[...]]` and embeds `![[...]]`: none. No image or attachment referenced, so the overwrite screenshot is not leaked.
- External URLs: 13 distinct, all on evidence.dev / docs.evidence.dev, each matching a Works Cited entry. Fetched and content-checked: editing, mcp/studio, analytics-agent, features/evidence-agent, features/version-control, publishing, cli, cli/connections, core-concepts/metrics, core-concepts/components, features/row-level-security, blog/evidence-core, blog/that-dashboard-should-be-a-skill. All 13 loaded.
- Works Cited: 13 entries, alphabetized, all cited inline. (Editing Decisions mentions "all ten"; the later Version Control and Publishing additions, plus Studio MCP, bring it to 13. Not a problem for the reader.)

## 8. Mechanical checks

Run in `/mnt/user-data/uploads/Evidence/Studio Feedback Package/`.

| Check | Command | Result |
|---|---|---|
| Hex (case-insensitive, all text incl. links and targets) | `grep -inc 'hex' *.md` | 0 in all five files |
| Em dash U+2014 | `grep -c $'\u2014' *.md` | 0 |
| En dash U+2013 | `grep -n $'\u2013' *.md` | 0 |
| Other non-ASCII | Python scan | Only curly quotes (13 pairs), one curly apostrophe (main note), middle dots used as link separators |
| TODO / FIXME / TBD / `%%` / `<!--` / `[[` / `![` | `grep -inE 'todo|fixme|tbd|xxx|\[\[|!\[|<!--|%%' *.md` | 0 |
| "Claude" / "Codex" | same grep with `claude|codex` | Only as disclosed tools (main note lines 3, 25, 43, 55; How I Used AI; Walkthrough step 6; Analysis 37; References 11). No assistant-chat leftovers |
| Frontmatter | `head -3` | None in any file |
| Double spaces | `grep -nE '[^ ]  +[^ ]' *.md` | 0 |
| Repeated words | `grep -niE '\b([a-z]+) \1\b' *.md` | 0 |
| Link and anchor resolution | Python: parse `[..](..)`, URL-decode, check file and heading | 26 of 26 resolve |
| Word counts | `wc -w` | Main 1,245; Walkthrough 1,390; Analysis 1,871; References 619; How I Used AI 131 |
| Bold formatting anomaly | manual read | References line 11 (M1) |

Terminology: "Evidence Studio", "Studio", "Studio MCP", "Analytics Agent", "Evidence Agent", "Evidence Core"/"Core" used consistently. "Agent View" and "IDE view" are Sam's terms (S1). "Error fix" used consistently per Sam's decision.

## 9. What I could not verify

- Time spent (self-report).
- Firsthand observations recorded only in Editing Decisions, not in the raw review log: the component inspector Results/SQL tabs, the published chat layouts and saving insights as reports, the two-way GitHub sync and the later pending-deletion state. I treat them as Sam's reports.
- Whether insights can actually be refined and saved to a "library" as standalone reports (not on any page I fetched; plausible from Sam's use).
- HLA-28's description of the render-and-fix loop was recorded by Claude; Sam's own corroboration is HLA-36.
- Whether the Google Docs versions match these Obsidian files, and in which format the package will be sent.
- Page checks rely on WebFetch summaries, not a manual full read.

## 10. Cold read as an Evidence engineer or PM

It makes sense without the companions. Within the first paragraph I know what was built, that it worked, what was good (agent grounded in my data, visible code) and the two asks. The Good / Stuck walkthrough is skimmable and honest. Tone is respectful and specific, with credit for existing features (settings, diff, inspector, Analytics Agent, MCP `visualize` loop), so it does not read as "you should add X".

Strongest point: Theme 2. Evidence already built the render-and-fix loop for external agents through Studio MCP, and the native agent asked for Accept with errors visible and said it had not looked at the rendered section. That is concrete, cheap to act on, and flattering to existing work.

What might confuse or annoy: the Step 8 tag (M2); "IDE view" as if it were an Evidence term (S1); Theme 1 is long, and the Agent View idea appears in paragraphs 2 and 4 with the Analytics Agent paragraph between them, so a reader may need a second pass to see that it is a question building on existing insights. Length is a little over target but not tiring.

## 11. Follow-through, 3 November 2026

The review above is preserved as written. This section records the subsequent revisions to the Google Docs and Obsidian package.

Sam clarified that he personally refined an insight draft and saved it as its own report in the library. He chose to keep the current detail and make light edits rather than trim toward 1,000 words.

| Item | Resolution |
|---|---|
| M1 | Fixed Rendering formatting in Google Docs and Markdown: label bold, body regular, visualize in code style. |
| M2 | Step 8 now points to Theme 3; the Git paragraph names the incoming-commit question and links to the fuller framework analysis. |
| M3 | Main, analysis, and walkthrough describe refining/saving as firsthand. References distinguishes those observations from the product page's documented shareable insights and report reuse, with a link to the walkthrough. |
| M4 | The two descriptions of McAskill's story now say customer-health. Sam's account-health scenario remains. |
| S1 | IDE view is defined on first use in the main note and analysis. |
| S2 | Rewrote What I built using Neon Postgres and two clearer sentences. |
| S3 | Feature-branch Publish wording now states the documented squash-commit/overwrite behavior without implying a warning block. |
| S4 | Agent capability now says read the data behind charts and tables. |
| S5 | Warning/error wording is now a tentative improvement tied to the observed prepared prompt. |
| S6 | Evidence Docs is italicized in the Studio MCP Works Cited entry. |
| S7 | Kept the detail at Sam's request; the main note is about 1,300 words. |
| S8 | Native Google Docs use links to the five documents and verified heading IDs; Markdown uses local note links. All 27 native cross-document links and corresponding Markdown targets were checked. No PDF was created. |

Optional polish: named Studio MCP's visualize tool in the main note and formatted it as code in the relevant documents; clarified that the temperature-format item was a warning while retaining Sam's preferred error-fix terminology; clarified the AI-use note's reference to agent evaluations. Preserved runtime as Sam's characterization, the future team-setup wish, and useful repetition in standalone companions. Retained the current division of Docs/Support observations rather than restoring material removed from the main Google Doc.

Verification: exact planned prose changes read back from all five Google Docs; original heading IDs and all nine existing comment threads preserved; formatting read back for Rendering, tool names, and the Studio MCP bibliography entry. The revised Google Docs were synced to all five Obsidian notes. No new live-product test, external send, or PDF export was performed.
