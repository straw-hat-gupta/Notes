Back to [Evidence Studio Feedback](Evidence%20Studio%20Feedback.md)

These are the sources behind the research-informed points in my notes. Under each citation, I explain what I took from it and what remains my interpretation. My firsthand experience is recorded in the [walkthrough](Walkthrough%20Details.md).

## Sources and how I used them

"Analytics Agent." *Evidence*, [evidence.dev/product/analytics-agent](https://evidence.dev/product/analytics-agent). Accessed 2 Nov. 2026.

Explains how readers can ask questions and save insights, with queries and sources behind answers and prompts and implementation notes kept with insights. I used this to recognize the provenance Evidence already provides while describing the fuller action/check history I wanted.

"CLI." *Evidence Docs*, [docs.evidence.dev/cli](https://docs.evidence.dev/cli). Accessed 2 Nov. 2026.

Describes local development with an agent of your choice and GitHub PR previews. It supports the idea of working with an Evidence project through familiar code workflows; I did not test this CLI route during the walkthrough.

"Components." *Evidence Docs*, [docs.evidence.dev/core-concepts/components](https://docs.evidence.dev/core-concepts/components). Accessed 2 Nov. 2026.

Describes reporting elements with typed attributes and validation. This grounds my point about a framework focused on BI, while leaving the correctness of a particular analysis to be checked.

"Connect Your CLI to Your Data." *Evidence Docs*, [docs.evidence.dev/cli/connections](https://docs.evidence.dev/cli/connections). Accessed 2 Nov. 2026.

Explains that the logged-in CLI uses the Studio organization's connection, credentials, and access rules. It does not by itself establish every project's effective access or whether hosted project-specific connection settings exist.

"Editing." *Evidence Docs*, [docs.evidence.dev/editing](https://docs.evidence.dev/editing). Accessed 2 Nov. 2026.

Documents the diff shown for agent edits and support for changing project/page settings. My feedback is about retaining chat and task context and making checks clear, not a claim that the agent cannot edit or repair reports.

"Evidence Agent." *Evidence Docs*, [docs.evidence.dev/features/evidence-agent](https://docs.evidence.dev/features/evidence-agent). Accessed 2 Nov. 2026.

Describes the project’s version-controlled agent context and on-demand skills. I noticed the agent directory but did not customize it; I used the documentation to understand how teams could maintain their own instructions and methods.

McAskill, Adam. "Evidence Core." *Evidence*, 26 Aug. 2026, [evidence.dev/blog/evidence-core](https://evidence.dev/blog/evidence-core). Accessed 2 Nov. 2026.

Introduces the framework powering Studio, including live warehouse queries, reusable metrics, and validation tooling. This supports the foundation behind my positive framework/runtime point. Its long-term adoption potential is my interpretation, not an outcome measured in this exercise.

---. "That Dashboard Should Be a Skill." *Evidence*, 7 Aug. 2026, [evidence.dev/blog/that-dashboard-should-be-a-skill](https://evidence.dev/blog/that-dashboard-should-be-a-skill). Accessed 2 Nov. 2026.

Describes an unnamed customer turning a complex account-health dashboard into a guided skill, using product usage, support, and renewal context. This informed my customer scenario. The data-team/customer-success roles are my interpretation, and the post does not establish measured benefits or the customer’s identity.

"Metrics." *Evidence Docs*, [docs.evidence.dev/core-concepts/metrics](https://docs.evidence.dev/core-concepts/metrics). Accessed 2 Nov. 2026.

Explains reusable metric definitions that carry the aggregation, filter, format, and label for components to inherit. This is a concrete example of shared reporting conventions; I did not test a shared-metric revision.

"Row Level Security." *Evidence Docs*, [docs.evidence.dev/features/row-level-security](https://docs.evidence.dev/features/row-level-security). Accessed 2 Nov. 2026.


Documents table and row access controls and directs direct-connector users to connector-specific rules. I used it to keep questions about investigation scope separate from claims about permission enforcement, which I did not test.
