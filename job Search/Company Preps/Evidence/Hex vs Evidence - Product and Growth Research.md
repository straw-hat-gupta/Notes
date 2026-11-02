# Hex vs Evidence — product value and growth

Research date: **2026-11-01**. Related: [[Product Review Plan]] · [[Product Review Findings]] · [[Customer Use Case Research]].

**Scope:** Public-source research, not a hands-on Hex evaluation. Product capabilities are documented/vendor-described; customer outcomes and adoption figures are attributed claims. Explanations of growth and workflow fit are labeled inferences. Undated docs, case studies, and pricing were accessed on the research date. No trials, purchases, or customer outreach were performed.

## Main findings

- **Hex has historically connected exploratory analysis to business consumption:** SQL/Python work, shared notebooks, published apps, and self-service questions. **Evidence emphasizes a reporting system maintained as code:** pages, components, definitions, configuration, and deployment. These are differences of emphasis, with substantial overlap; the comparison below supplies the source evidence.
- **The distinction is converging.** Hex announced a code-backed 4.0 architecture on October 27, 2026. Its private-beta status matters: do not compare all classic Hex features and all announced 4.0 capabilities as if they were one generally available product.
- **Evidence's strongest supported advantages are its open-source Core and documented repository/local-development workflow.** Hex offers a broader integrated analytical workspace and explicit in-product review/self-service journeys. Which saves more work is still a task-specific hypothesis.
- **Hex's growth plausibly combines a useful analyst entry point, expansion to business users, distribution, and investment.** The public evidence does not isolate the causal contribution of any one feature or establish audited revenue growth.

## Important release boundaries

**Evidence Core and Studio:** The August 26, 2026 announcement describes an open-source foundation shared with Studio. Core includes live warehouse queries, reusable metrics, a validator/CLI, and container self-hosting. Studio adds hosted development, distribution, page-level access, its analytics agent, and hosted MCP. Live queries and metric reuse should not be presented as uniquely Studio benefits. [Evidence Core](https://evidence.dev/blog/evidence-core)

**Hex classic versus 4.0:** The October 27 launch describes code-file-backed projects, external-agent editing, and an inspectable dependency graph. It claims a rebuilt execution engine, but its internal speed examples are not independent benchmarks. [Introducing Hex 4.0, 2026-10-27](https://hex.tech/blog/introducing-hex-4-0/)

The current 4.0 guide says **private beta**, with access requested by workspace admins. It documents SQL/Python/TypeScript logic and external-agent build/preview/publish workflows. Its unsupported-feature list includes scheduled runs, app notifications, Chat with App, PDF export, Slack agent integration, and other items. Existing classic projects continue separately. Verify the project type and entitlements before testing a feature. [Hex 4.0 guide](https://learn.hex.tech/docs/hex-4-0/what-is-hex-4-0)

## Product comparison

The Hex column describes the documented classic product unless explicitly marked 4.0. **A documented feature is not proof that its experience is better.**

| Workflow | Hex | Evidence | Value to investigate |
|---|---|---|---|
| Explore and build | Notebook cells combine SQL, Python, and no-code analysis; selected cells become a published app. [Hex 101](https://learn.hex.tech/tutorials/quickstart/hex-basics) | Markdown/SQL/component pages form a code-defined reporting project. [Evidence](https://evidence.dev/) | Hex may suit iterative analytical work crossing languages; Evidence may suit a maintained collection of reports without building the visual layer from scratch. |
| Nontechnical questions | Threads provides conversational analysis; Chat with App works from published analyses. [Hex 101](https://learn.hex.tech/tutorials/quickstart/hex-basics) | The Evidence Agent uses report/query context to answer readers and generate insights, respecting access rules. [Evidence Agent](https://docs.evidence.dev/features/evidence-agent) | “Users can ask questions” is shared capability. Compare useful answers, traceability, permissions, and handoff to a maintained report. |
| Review and collaboration | Native review requests, comments, approvals, and requested changes on Team/Enterprise. Privileged users can override required reviews. [Hex Reviews](https://learn.hex.tech/docs/collaborate/reviews) | Shared Studio working state; own-repo workflows integrate local changes and Git-based review/publishing. [Evidence Version Control](https://docs.evidence.dev/features/version-control) | Can a less technical reviewer complete the task without learning Git? Neither workflow should be assumed conflict-proof or impossible to bypass. |
| Roles and access | Workspace roles determine allowed resource permissions and distinguish Editor, Explorer, and Viewer workflows. [Hex roles](https://learn.hex.tech/docs/collaborate/sharing-and-permissions/roles) | Page grants govern reader access; Developer, Admin, and Org Viewer can view all pages regardless of those grants. [Evidence page access](https://docs.evidence.dev/features/page-level-access-control) | Test viewing, editing, reviewing, and data-source access separately; a role label alone does not establish the intended isolation. |
| Repository workflow | Classic Git Export produces YAML and is documented as one-way, not external Git round-trip editing; it also has branch-protection restrictions. [Hex Git Export](https://learn.hex.tech/docs/explore-data/projects/git-export) | A connected GitHub repo can be edited from Studio or locally. [Evidence Version Control](https://docs.evidence.dev/features/version-control) | Evidence's own-repo path differs materially from classic export. Do not apply classic limitations to 4.0 without checking its file/CLI workflow. |
| External AI agents | MCP documents project creation/editing/execution for Editor+; Team/Enterprise and beta conditions apply. [Hex MCP](https://learn.hex.tech/docs/api-integrations/mcp-server) | Current Studio MCP lists read/query/render tools, without a save-page tool. Local Core/CLI authoring is a separate route. [Studio MCP](https://docs.evidence.dev/mcp/studio) | A concrete test of the manual-handoff issue observed in the homelab run; “both have MCP” hides different action scopes. |
| Reusable business context | Context Studio manages guides, endorsements, models, observability, and eval workflows. [Hex Context Studio](https://learn.hex.tech/docs/agent-management/context-studio) | Context and on-demand analytical skills live in the version-controlled `agent/` directory; external clients can retrieve them. [Evidence Agent](https://docs.evidence.dev/features/evidence-agent) | Compare the effort to encode a definition once, detect a wrong answer, and improve behavior. Do not assume governance exists only in Hex. |

**Code portability needs a precise definition.** Evidence documents a self-hostable open-source runtime, which is stronger than merely exporting a project file. Hex supports readable YAML export/import for classic projects, including file-format validation; 4.0 uses code files. Neither of those facts alone establishes an equivalent open-source self-hosted Hex runtime. [Evidence Core](https://evidence.dev/blog/evidence-core), [Hex import/export](https://learn.hex.tech/docs/explore-data/projects/import-export), [Hex 4.0 launch](https://hex.tech/blog/introducing-hex-4-0/)

**Git is not an automatic safety advantage for either product.** Hex classic export explicitly requires a compatible repository without review-enforcing branch protection. Evidence's own-repo workflow can use PR review, but Sam encountered an overwrite confirmation (working finding F01). These are different mechanisms; test them rather than equating “has Git integration” with safe mixed-author collaboration. [Hex Git Export](https://learn.hex.tech/docs/explore-data/projects/git-export) · [[Product Review Findings#F01 — Publishing asks the user to judge an overwrite risk|F01]]

**GitHub/versioning follow-up (2026-11-01):** Hex also has built-in saved-version history and restoration; Professional history is limited to 30 days. Classic Git export remains a one-way YAML audit trail, not automatic ingestion of external project edits. Separately, Context Sync supports Git/CI-managed guides, semantic projects, and evals flowing into Hex, read-only there; GitHub Actions can preview PR context changes. Thus “Hex cannot use Git as a source of truth” is too broad: distinguish report projects from agent/model context. CLI project editing and 4.0 code files also prevent claiming that external authoring is unavailable; an equivalent repo-driven report edit/PR/deploy workflow remains unverified for 4.0. [History](https://learn.hex.tech/docs/explore-data/projects/history-and-versions), [Git export](https://learn.hex.tech/docs/explore-data/projects/git-export), [Context Sync](https://learn.hex.tech/docs/agent-management/context-management/context-sync), [CLI](https://learn.hex.tech/docs/api-integrations/cli), [4.0](https://learn.hex.tech/docs/hex-4-0/what-is-hex-4-0)

### Connections, projects, and data access

**Follow-up checked 2026-11-01, prompted by HLA-43.** Hex explicitly documents workspace-shared and project-only connections; a project can use multiple sources. Evidence's consulted docs describe organization-level data setup, but no per-project Studio connection assignment was established. This is a documented Hex capability versus an unresolved Evidence question. [Hex connection scopes](https://learn.hex.tech/docs/connect-to-data/data-connections/data-connections-introduction), [Multiple sources](https://learn.hex.tech/docs/getting-started/connect-your-data), [Evidence connections](https://docs.evidence.dev/cli/connections)

| Control | Hex | Evidence boundary established so far |
|---|---|---|
| Central reuse and administration | Workspace connections can be shared with selected user groups; admins can inspect which projects import an asset. [Workspace assets](https://learn.hex.tech/docs/administration/workspace_settings/workspace-assets) | Studio's organization connection and credentials are reused; creating a project has not been shown to create an isolated data environment. |
| Project-local connection | Hex documents project-only connections. Enterprise admins can disable creation of new project connections without removing existing ones. [Workspace security](https://learn.hex.tech/docs/administration/workspace_settings/workspace-security) | A local `connection.yaml` overrides the Studio organization connection for CLI use; this does not establish per-project hosted Studio scoping. [Evidence connections](https://docs.evidence.dev/cli/connections) |
| Author versus result access | Connection Can query controls query authoring. Enterprise Can view results can block project access even when it was shared. Without that extra restriction, a person may be allowed to consume an app while lacking connection query-authoring permission. [Hex connection permissions](https://learn.hex.tech/docs/connect-to-data/data-connections/data-connections-introduction), [Project sharing](https://learn.hex.tech/docs/collaborate/sharing-and-permissions/project-sharing) | Page grants and underlying table/row rules are separate layers; direct connectors require checking connector-specific enforcement. [Evidence data access](https://docs.evidence.dev/features/row-level-security) |
| Database identity | Enterprise OAuth can require a user's own warehouse identity on supported Snowflake, Databricks, and BigQuery connections. This is not a documented Neon/Postgres capability. [OAuth](https://learn.hex.tech/docs/connect-to-data/data-connections/oauth-data-connections) | The direct Postgres connector runs queries as its configured database user; per-viewer identity mapping is not currently documented as supported. [Postgres](https://docs.evidence.dev/direct-connectors/postgres) |

**Interpretation:** Hex makes connection scope and author-versus-consumer access more explicit in the consulted documentation. Its recommended shared-connection path is still centrally administered, so the distinction is not simply “Hex projects own data, Evidence organizations own data.” Selecting/importing a workspace connection into a project is also different from an administrator restricting that connection to an approved set of project IDs; the latter control has not been established here. Schema-browser filtering is not proof of enforced query restrictions.

**Next comparison:** With synthetic public/sensitive tables and two accounts, test connection discovery, adding it to a project, authoring a query, viewing a shared output, and asking an agent follow-ups. Record database grants, user/group permissions, plan, and Hex classic/4.0 behavior separately. Do not infer unrestricted access from an empty metadata-tool response or a missing documentation page. No permission test was run.

## Where each may provide more value

**Hex — inference from the documented workflows:** A data team investigating why activation fell can move between SQL exploration, Python analysis, an interactive app for Product, and subsequent self-service questions in a common workspace. Its potential advantage is reducing handoffs across analytical and business roles. The key comparison is the whole question-to-decision process, not chart count. [Hex 101](https://learn.hex.tech/tutorials/quickstart/hex-basics)

**Evidence — inference from the documented architecture:** A team already treating reporting as software can keep reports and conventions in its development workflow, use an open-source deployment route, and choose Studio when managed authoring and platform services are useful. This may be valuable when ownership, versionable reporting conventions, and deployment flexibility matter. It is not proof that maintenance is easier; the homelab findings expose gaps to test. [Evidence self-hosting and platform tradeoffs](https://docs.evidence.dev/self-host), [Evidence Version Control](https://docs.evidence.dev/features/version-control)

**Competitive implication:** “Code is easier for agents to work with” is increasingly a category thesis, not an exclusive Evidence differentiator. Hex 4.0 targets that premise too. Evidence's case needs to rest on the practical experience of building, inspecting, sharing, maintaining, and deploying trusted reporting—not only the fact that files exist in a repo. This is analysis, not a measured competitive win.

## Pricing and adoption friction

| Public offering | Listed model on 2026-11-01 |
|---|---|
| Hex Community | Free, with limited features/compute and an agent trial |
| Hex Professional | $36 per Editor/month |
| Hex Team | $75 per Editor/month; advanced compute and other entitlements can add cost |
| Evidence Core | Open source/self-hosted; infrastructure and operational effort remain |
| Evidence Studio Team | $2,500/month, unlimited users, 20K AI credits |
| Enterprise use | Both list custom Enterprise offerings; Hex embedding is an add-on there, while Evidence lists embedding/whitelabelling under Enterprise |

Sources: [Hex pricing](https://hex.tech/pricing/), [Evidence pricing](https://evidence.dev/pricing), [Evidence self-hosting costs](https://docs.evidence.dev/self-host).

**Interpretation:** Hex has a lower listed hosted entry point for a small author team; Evidence's flat hosted model has different economics as the audience grows. Core also provides a free-software entry route. Do not infer that Evidence lacks product-led adoption or that one is cheaper at every team size. Model the actual author/explorer/viewer mix, AI credits, compute, warehouse costs, and required Enterprise features. These prices are not a like-for-like total-cost comparison or historical evidence of what drove earlier growth.

## What is established about Hex's scale?

| Date | Public evidence | What it establishes |
|---|---|---|
| 2022-03-22 | $52M Series B; the founder described thousands of individual users and a collaborative analysis-to-app workflow. [Series B](https://hex.tech/blog/series-b/) | Meaningful adoption and the core product thesis predated the recent agent launches. Users are not the same measure as customer accounts. |
| 2025-05-28 | Over 1,500 teams; $70M Series C. [Series C](https://hex.tech/blog/series-c/) | A dated company-reported adoption milestone and financing event, not audited ARR. |
| 2026-10-27 | Over 2,500 customers; $100M financing at a $1.2B valuation. The founder identifies team growth and go-to-market as uses of the capital. [New-era announcement](https://hex.tech/blog/hex-new-era/) | A newer dated scale claim and additional investment. Valuation/funding are not customer revenue or product profitability. |

The same October announcement describes external-agent friction in the older architecture as a motivation for the rewrite. This is useful evidence that scale does not mean every workflow is already solved. The new beta is a response to emerging needs, not an explanation of all adoption achieved before its release. [New-era announcement, 2026-10-27](https://hex.tech/blog/hex-new-era/)

**Limits:** No audited ARR, retention, customer-acquisition cost, channel attribution, or consistent paid-customer cohort series was established. “Teams,” “customers,” and individual users have different definitions; do not calculate a precise growth rate from these milestones. Evidence reports Studio adoption in hundreds of organizations and Core adoption in thousands, but those aggregate populations are not directly comparable with Hex's count. [Evidence About](https://evidence.dev/about)

## Plausible contributors to Hex's growth

These are explanations supported to different degrees, not isolated causal findings.

### 1. A useful analyst entry point that produces something other people can use

**Observed:** The 2022 product story already combined coding, multiplayer work, shareable apps, and a discoverable library. This was a workflow proposition before modern conversational agents. **Inference:** Solving both analysis and delivery gave teams more reasons to keep using Hex than a standalone notebook or chart generator. [Series B, 2022-03-22](https://hex.tech/blog/series-b/)

### 2. Expansion beyond the original analyst audience

**Reported case:** Notion's story says 86% of recent Notebook Agent users were not data scientists. It describes business teams finding data and using apps alongside advanced analyst work. That percentage concerns agent users, not 86% of Notion's employees, and the customer still has other analytics tools. **Inference:** An analyst foothold can spread to recurring business workflows and more internal users. It does not establish Hex's company-wide expansion revenue. [Notion case, undated](https://hex.tech/customers/notion/)

### 3. Getting the output into everyday work

**Reported case:** Ramp describes co-creation by Product/data staff, apps placed in Salesforce and Notion, and feedback cycles shortened from two days to hours. These are vendor-hosted customer statements, not controlled measurements. **Inference:** Repeated use where decisions occur can support adoption better than requiring everyone to visit another dashboard portal. This directly addresses the “what happens after publishing?” question in HLA-41. [Ramp case, undated](https://hex.tech/customers/ramp/)

### 4. A combination of accessible entry and implementation partners

**Observed:** Current pricing supplies free/individual/team entry points. The consulting program launched January 28, 2025 offers Enterprise access, training, referral commissions, and co-selling support. **Inference:** Individuals can try the product, while consultants can introduce and implement it for organizations. The program's existence is established; its sourced pipeline and revenue contribution are not. Evidence's open-source route is another adoption mechanism, so the comparison should investigate conversion and activation rather than assume only Hex has a funnel. [Hex pricing](https://hex.tech/pricing/), [Consulting partnership launch](https://hex.tech/blog/hex-consulting-partnership-program/)

### 5. Resources and deliberate broadening of the product

**Observed:** Hex acquired Hashboard on April 30, 2025, identifying self-service BI, semantic modeling, visualization, and performance as areas it wanted to strengthen. **Inference:** Acquisition added expertise to extend beyond its initial notebook workflow; no acquisition-attributed revenue uplift was established. [Hashboard announcement](https://hex.tech/blog/welcoming-hashboard/)

The financing milestones provide resources for product and distribution investment. They do not establish that capital caused adoption, that every release worked, or that Evidence needs to reproduce Hex's entire scope.

**Best-supported explanation:** Hex's combination of deep analytical work and reusable business-facing outputs appears to enable adoption across roles. Product packaging, distribution, partners, and capital plausibly reinforce that loop. Customer studies support the workflow mechanism; private commercial data would be needed to rank its contribution against sales execution, market timing, or other factors.

## Implications for the Evidence review

| Existing finding/question | Research adds | What still needs testing |
|---|---|---|
| F08: Claude required manual page handoff | Hex documents MCP authoring, and 4.0 specifically documents external-agent build/preview/publish. [Hex MCP](https://learn.hex.tech/docs/api-integrations/mcp-server), [4.0 guide](https://learn.hex.tech/docs/hex-4-0/what-is-hex-4-0) | Can the authorized tools actually finish the equivalent task without copy/paste? Record classic versus beta. |
| F01/Q3: Git and less technical maintenance | Hex has an explicit native review journey, but privileged overrides and classic Git-export restrictions remain. [Reviews](https://learn.hex.tech/docs/collaborate/reviews) | Which workflow lets a novice request/receive review safely? Do not presume Hex solves the overwrite scenario. |
| P01/Q1: useful data-grounded suggestions | Both products connect questions to existing analytical context; governance is part of the comparison, not a unique checkbox. [Hex Context Studio](https://learn.hex.tech/docs/agent-management/context-studio), [Evidence Agent](https://docs.evidence.dev/features/evidence-agent) | Encode the same business definition and deliberate ambiguity, then inspect both answers. |
| F04/F07: readiness and trustworthy output | Hex 4.0 advertises inspectable logic/lineage; that is a review aid, not proof of correct calculations. [4.0 launch](https://hex.tech/blog/introducing-hex-4-0/) | Use known NULL/unsupported data and incorrect aggregations; inspect warning and review behavior. |
| HLA-41: value after creating a report | Ramp supplies a concrete distribution/decision workflow to emulate. | Can a recipient use the report and complete a decision without the author guiding them? |

## Next comparisons to run

1. **Question → analysis → report:** Same synthetic product data, one known issue, one narrative report and filter. Compare setup, discovery, correctness, manual interventions, and reader comprehension. Add a Python-heavy variant only if it represents an actual target use case.
2. **External-agent completion:** Give Claude the same minimal goal in each platform. Compare the full path through creation, render checking, revision, review, and publication, with permissions/plan/project type recorded.
3. **Nontechnical review and ongoing maintenance:** A second participant requests a metric change and reviews it. Test missing data and a changed shared definition. Use a disposable project for Git divergence and recovery.
4. **Distribution and repeat use:** Deliver a dated report, use it in a short review, then ask a follow-up question after the data changes. Explicitly check beta feature availability rather than mix classic and 4.0 results.

Record time to a correct useful result, docs/help visits, steps outside the product, manual transfers, assumptions, repair effort, role confusion, and later maintenance. Raw error count or chart appearance alone is not a sufficient score. No comparative runs have been completed as part of this research.

## Questions worth asking Evidence

- When a customer compares current Studio with Hex, which workflow and buyer requirement actually wins the deal?
- Which customers choose Core/self-hosting or own-repo development, and what measurable work does that save?
- Who begins using Evidence, who subsequently joins, and where do activation or expansion stall?
- Is external-agent page/diff authoring part of the intended Studio workflow, or should users move to CLI/Git for that task?
- How should a less technical author request review and publish safely when developers also work in Git?
- As both platforms move toward code-backed agent workflows, which advantage should Evidence make unmistakable in the first session?

**Research status:** Product comparison and first-pass growth analysis completed from primary sources. Actual comparative usability, Hex 4.0 rollout experience, exact total costs, and causal revenue-growth attribution remain open. Feed validated conclusions into [[Product Review Findings]]; keep research claims separate from Sam's hands-on observations.
