Back to [Evidence Studio Feedback](Evidence%20Studio%20Feedback.md)

## Research notes

These are the sources behind the research-informed points in my feedback. The explanations use inline MLA citations; the complete bibliography is below. My firsthand experience is recorded in the [walkthrough](Walkthrough%20Details.md).

**The framework.** Evidence Core powers Studio and combines live warehouse queries, reusable metrics, and validation tooling ([McAskill, “Evidence Core”](https://evidence.dev/blog/evidence-core)). The component system provides reporting elements with typed attributes and validation (["Components"](https://docs.evidence.dev/core-concepts/components)). Metric definitions can carry an aggregation, filter, format, and label for components to inherit (["Metrics"](https://docs.evidence.dev/core-concepts/metrics)). These are concrete foundations for my shared-framework idea; wider adoption is my interpretation, and I did not test a shared-metric revision.

**The agent and authoring workflow.** Project instructions and on-demand skills can be version-controlled; I noticed the agent directory but did not customize it (["Evidence Agent"](https://docs.evidence.dev/features/evidence-agent)). Local development with an agent of your choice and GitHub PR previews are documented, although I did not test that CLI route (["CLI"](https://docs.evidence.dev/cli)). The editor already shows a diff and supports project/page settings changes, so my integration wish concerns chat/task continuity rather than a lack of editing capabilities (["Editing"](https://docs.evidence.dev/editing)). Queries and sources behind answers, plus prompts and implementation notes saved with insights, are also documented; I wanted a fuller record of actions and checks I could revisit (["Analytics Agent"](https://evidence.dev/product/analytics-agent)).

**Data scope.** The logged-in CLI uses the organization's connection, credentials, and access rules, but that alone does not establish every project's effective access or its hosted scoping options (["Connect Your CLI to Your Data"](https://docs.evidence.dev/cli/connections)). Table and row access controls are documented separately, with connector-specific rules for direct connections (["Row Level Security"](https://docs.evidence.dev/features/row-level-security)). I did not test those controls; choosing data for an investigation and enforcing access remain separate questions.

**The customer example.** Evidence describes an unnamed customer turning a complex account-health dashboard into a guided skill, using product usage, support, and renewal context ([McAskill, “That Dashboard”](https://evidence.dev/blog/that-dashboard-should-be-a-skill)). That informed my scenario of a data team maintaining analysis for customer-success colleagues. Those roles are my interpretation, not disclosed details about the customer, and the post does not establish measured benefits.

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

"Row Level Security." *Evidence Docs*, [docs.evidence.dev/features/row-level-security](https://docs.evidence.dev/features/row-level-security). Accessed 2 Nov. 2026.
