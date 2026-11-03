Back to [Evidence Studio Feedback](Evidence%20Studio%20Feedback.md)

## Research notes

These are the sources behind the research-informed points in my feedback. The explanations use inline MLA citations; the complete bibliography is below. My firsthand experience is recorded in the [walkthrough](Walkthrough%20Details.md).

**The framework.** Evidence Core powers Studio and combines live warehouse queries, reusable metrics, and validation tooling ([McAskill, “Evidence Core”](https://evidence.dev/blog/evidence-core)). The component system provides reporting elements with typed attributes and validation (["Components"](https://docs.evidence.dev/core-concepts/components)). Metric definitions can carry an aggregation, filter, format, and label for components to inherit (["Metrics"](https://docs.evidence.dev/core-concepts/metrics)). These are the BI foundations I valued, alongside the familiar development workflow described below.

**The agent and authoring workflow.** Project instructions and on-demand skills can be version-controlled; I noticed the agent directory but did not customize it (["Evidence Agent"](https://docs.evidence.dev/features/evidence-agent)). Local development with an agent of your choice and GitHub PR previews are documented, although I did not test that CLI route (["CLI"](https://docs.evidence.dev/cli)). The agent already shows a diff and can adjust project/page settings, so my integration wish concerns help with surrounding Studio workflows and chat/task continuity (["Editing"](https://docs.evidence.dev/editing)). The Analytics Agent answers questions, builds shareable insights that can be saved as standalone reports, and keeps the prompt and implementation notes with each insight. Insight content can also be reused in maintained pages. This supports the reader workflow I appreciated, alongside my wish for a clearer record of checks on edits (["Analytics Agent"](https://evidence.dev/product/analytics-agent)).

**Rendering. Studio MCP documents visualize for rendering Evidence components and Markdown. Claude used it to check its page during my separate build; I did not establish how the native Studio agent accesses that tool (**[**"Studio MCP"**](https://docs.evidence.dev/mcp/studio)**).**

**Data scope.** The logged-in CLI uses the organization's connection, credentials, and access rules, but that alone does not establish every project's effective access or its hosted scoping options (["Connect Your CLI to Your Data"](https://docs.evidence.dev/cli/connections)). Table and row access controls are documented separately, with connector-specific rules for direct connections (["Row Level Security"](https://docs.evidence.dev/features/row-level-security)). I did not test those controls; choosing data for an investigation and enforcing access remain separate questions.

**The customer example.** Evidence describes an unnamed customer turning a complex account-health dashboard into a guided skill, using product usage, support, and renewal context ([McAskill, “That Dashboard”](https://evidence.dev/blog/that-dashboard-should-be-a-skill)). That informed my scenario of a data team maintaining analysis for customer-success colleagues. Those roles are my interpretation, not disclosed details about the customer, and the post does not establish measured benefits.

**Versioning and publishing.** Evidence documents main-only development for solo work and feature branches for teams. Studio edits are held in a shared working state before commit; a development branch can be committed and then published from Studio or reviewed and merged through a GitHub PR. The docs warn that the Studio Publish path can overwrite published-branch changes (["Version Control"](https://docs.evidence.dev/features/version-control)). PRs receive Markdown and access-rule checks plus a preview; merging into the published branch triggers publication (["Publishing"](https://docs.evidence.dev/publishing)). This informed my question about bringing incoming GitHub changes into an unpublished Studio draft and following the documented team workflow.

## Works Cited

"Analytics Agent." *Evidence*, [evidence.dev/product/analytics-agent](https://evidence.dev/product/analytics-agent). Accessed 2 Nov. 2026.

"CLI." *Evidence Docs*, [docs.evidence.dev/cli](https://docs.evidence.dev/cli). Accessed 2 Nov. 2026.

"Components." *Evidence Docs*, [docs.evidence.dev/core-concepts/components](https://docs.evidence.dev/core-concepts/components). Accessed 2 Nov. 2026.

"Connect Your CLI to Your Data." *Evidence Docs*, [docs.evidence.dev/cli/connections](https://docs.evidence.dev/cli/connections). Accessed 2 Nov. 2026.

"Editing." *Evidence Docs*, [docs.evidence.dev/editing](https://docs.evidence.dev/editing). Accessed 2 Nov. 2026.

"Evidence Agent." *Evidence Docs*, [docs.evidence.dev/features/evidence-agent](https://docs.evidence.dev/features/evidence-agent). Accessed 2 Nov. 2026.

McAskill, Adam. "Evidence Core." *Evidence*, 26 Aug. 2026, [evidence.dev/blog/evidence-core](https://evidence.dev/blog/evidence-core). Accessed 2 Nov. 2026.

---. "That Dashboard Should Be a Skill." *Evidence*, 7 Aug. 2026, [evidence.dev/blog/that-dashboard-should-be-a-skill](https://evidence.dev/blog/that-dashboard-should-be-a-skill). Accessed 2 Nov. 2026.

"Metrics." *Evidence Docs*, [docs.evidence.dev/core-concepts/metrics](https://docs.evidence.dev/core-concepts/metrics). Accessed 2 Nov. 2026.

"Publishing." *Evidence Docs*, [docs.evidence.dev/publishing](https://docs.evidence.dev/publishing). Accessed 3 Nov. 2026.

"Row Level Security." *Evidence Docs*, [docs.evidence.dev/features/row-level-security](https://docs.evidence.dev/features/row-level-security). Accessed 2 Nov. 2026.

"Studio MCP." Evidence Docs, [docs.evidence.dev/mcp/studio](https://docs.evidence.dev/mcp/studio). Accessed 2 Nov. 2026.

"Version Control." *Evidence Docs*, [docs.evidence.dev/features/version-control](https://docs.evidence.dev/features/version-control). Accessed 3 Nov. 2026.
