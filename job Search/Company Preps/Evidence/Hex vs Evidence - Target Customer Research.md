# Hex vs Evidence: target customer research

Research date: **2026-11-02**. Copy of the Claude Doc [Hex vs Evidence: target customer research](https://claude.ai/artifact/BvGsmju9j1JyMsrqXMmg7W). Related: [[Target Market and Customer Needs]] · [[Customer Use Case Research]] · [[Hex vs Evidence - Product and Growth Research]]

**Hex and Evidence sell to the same core customer: a modern-stack data team that must give business colleagues trusted numbers and, now, AI answers.** They split on the builder's starting job. Hex starts from exploratory SQL and Python and ships apps and actions to operators. Evidence starts from recurring reporting maintained as code and ships reports, skills, and embeds. Hex has much more public proof that its output changes operators' work; Evidence has the stronger ownership and review story but thin public outcome evidence. Both are converging on code-backed, agent-built analytics, which makes reviewing agent-made changes a shared, durable problem.

## Method

I applied the method from [[Target Market and Customer Needs]] to Hex: product, then workflow, surrounding stack, roles, deliverables, and value delivered or missing. Sources are Hex's site, docs, customer stories, pricing, and its October 2026 strategy post, read on 2026-11-02, plus the vault notes for Evidence. **Documented** means a vendor page states it; **customer-reported** means a quote on a vendor site; **inference** is my reading and is labeled. No product trials, outreach, or hands-on tests were done.

## Evidence recap (from the vault notes)

The notes (Target Market and Customer Needs, Customer Use Case Research, Hex vs Evidence, all dated 2026-10-31 to 2026-11-02) frame Evidence's customer as **an organization that wants its data team to own a reusable analytics system whose outputs people who do not maintain code can use**. This section restates them so the comparison has a baseline; they were not re-verified.

| Dimension | Evidence, per the notes |
| --- | --- |
| Products | Core (open-source framework, self-hostable), Studio (hosted authoring, agent, MCP, page access), Embedded, Enterprise controls |
| Core workflows | W1 maintain a recurring report as models change; W2 turn a specialist procedure into guided self-service (skills); W3 ship analytics inside a product; W4 explain a released dataset |
| Maintainer roles | Senior data/product analyst, analytics engineer, data/platform engineer, app engineer for embeds |
| Consumer roles | CS and commercial operators, Product, Finance, leadership, external customers |
| Surrounding stack | Warehouse (Snowflake, BigQuery, Postgres), dbt, GitHub, Fivetran-backed source syncs, Slack/email PDF delivery, Claude/Cursor via CLI and MCP |
| Deliverables | KPI reports, executive narratives, account assessments, embedded customer reports, release-quality reports |
| Pricing shape | Core free; Studio Team $2,500/month flat with unlimited users; embedding under Enterprise |
| Named evidence | Existence (job post), Every Cure (release dashboards), Brighthive (open-source agent output), Flipside (partner), Fluid Attacks (non-adopter) |

The working value proposition in the notes: a shared reporting language and runtime that makes data-team expertise reusable while keeping maintenance in a reviewable development workflow.

## Hex target customer

**Best-supported hypothesis (inference):** Hex targets data teams at venture-backed software and fintech companies, roughly 100 to 2,000 employees, who do exploratory SQL and Python analysis and then push the results to business teams as apps, chat answers, and self-serve exploration. Its published stories almost all start with a data scientist or analytics engineer and end with GTM, CS, or product staff consuming the output.

### Products as evidence of who it serves

| Product | What Hex documents | Customer implication (inference) |
| --- | --- | --- |
| [Notebooks + Notebook Agent](https://hex.tech/) | SQL, Python, and no-code cells; agent writes and refactors | Entry point is an analyst or data scientist doing open-ended work, often in Python |
| [Data apps + App Agent](https://hex.tech/) | Selected cells become an interactive app | The analyst ships a tool, not just a chart; consumers are operators |
| [Threads](https://learn.hex.tech/docs/explore-data/threads), Explore, BI | Conversational analysis and self-serve exploration | Expands to non-technical users; competes with Looker and Tableau seats |
| [Semantic models](https://learn.hex.tech/docs/connect-to-data/semantic-models/intro-to-semantic-models) + [Context Studio](https://learn.hex.tech/docs/agent-management/context-studio) | Workbench, YAML, sync from dbt MetricFlow, Cube, Snowflake Semantic Views; guides, endorsements, evals, governed mode | Analytics engineers are asked to maintain context so agent answers stay trustworthy |
| [Signed embedding](https://learn.hex.tech/docs/share-insights/embedding/signed-embedding) | Enterprise add-on; server-side presigned URLs; row filtering via user attributes in parameterized SQL | Customer-facing analytics is a secondary, enterprise-gated use |
| [MCP, API, CLI, 4.0](https://hex.tech/blog/hex-new-era/) | External agents (Claude, Cursor, Codex) read and build; 4.0 is code-file backed, private beta per the 2026-11-01 note | Hex is chasing the same "code is agent friendly" thesis as Evidence |

**Pricing shape** ([pricing](https://hex.tech/pricing/), checked 2026-11-02): Community free; Professional $36 per Editor per month; Team $75 per Editor per month; Enterprise custom with Explorer seats, OAuth warehouse identity, SSO, audit logs, and the embed add-on. This is a per-author model that starts small and expands seat by seat.

### Documented workflows (customer-reported, vendor-hosted)

| Customer | Builder | Consumer | Workflow and deliverable | Reported outcome |
| --- | --- | --- | --- | --- |
| [EliseAI](https://hex.tech/customers/eliseai/) | Analytics engineer; strategy and ops lead | CS, sales, SDRs (14 teams) | Snowflake + dbt + Salesforce app that generates QBR and audit slide decks; Threads for ad hoc account questions | QBR prep 2 days to 5 minutes |
| [Supabase](https://hex.tech/customers/supabase/) | Billing engineer, PM, data team | Support, finance, account teams | Billing command center with an approve-refund button calling an API; fraud playbook posting to Slack; churn score; 50-dashboard weekly review | Billing tickets 92% faster; about $300K fraud prevented |
| [Ramp](https://hex.tech/customers/ramp/) | Analytics engineers and data scientists in product pods | PMs, wider org | Sentiment analysis over Zendesk, surveys, Datadog; apps embedded in Salesforce and Notion | Feedback loops from 2 days to hours |
| [Notion](https://hex.tech/customers/notion/) | Data science team | Sales, CX, product, ops, finance | Notebook Agent for table discovery; Snowpark Python; account research app for sales; still runs Amplitude and Tableau | 86% of agent users not data scientists |
| [Inventa](https://hex.tech/customers/inventa/) | Data team, no engineering | Thousands of external suppliers | Replaced CSV to Python to PDF to Drive with parameterized supplier links on dbt semantic layer metrics | Daily instead of weekly insights |

All figures are customer statements on Hex's own site with no stated method. The [customer index](https://hex.tech/customers/) lists about 38 stories; by my count 22 are tech and software, 5 financial services, 3 healthcare and life sciences, and none are government or public sector.

### Roles, backgrounds, data, deliverables

- **Builders:** data scientists, analytics engineers, heads of data, plus technical non-data staff (billing engineers, PMs). Backgrounds lean statistics, Python, SQL. Job-search snippets for roles naming Hex pair it with dbt and Snowflake and treat it as the BI surface; I did not open those postings, so treat this as a lead, not a finding.
- **Consumers:** CS, sales, SDRs, support, finance, PMs, leadership, occasionally external partners.
- **Data:** cloud warehouse first (16 documented connectors including Snowflake, BigQuery, Databricks, Postgres, MotherDuck, ClickHouse per [connections docs](https://learn.hex.tech/docs/connect-to-data/data-connections/data-connections-introduction)); dbt models; CRM, support, product events; increasingly unstructured text.
- **Deliverables:** interactive apps, generated slide decks, Slack alerts, forecasts and ML scores, ad hoc answers, and fewer classic static dashboards.

### Integrations versus adjacent unintegrated tools

- **Integrated (documented):** warehouses above, dbt Cloud metadata and Semantic Layer, Cube and Snowflake semantic sync, GitHub and GitLab, Airflow, Dagster, Prefect, Slack, Claude, ChatGPT, Codex, Cursor via MCP ([homepage](https://hex.tech/)).
- **Adjacent, reached by workaround (inference from stories):** Salesforce and Notion receive Hex output by embedding or links, not a native write-back; Supabase reaches its refund API from Python cells; slide decks are generated, not round-tripped in PowerPoint. Customers keep Amplitude, Tableau, and Looker alongside Hex, so Hex rarely replaces the whole BI estate.

## Overlap

**The overlap is large and growing: a modern-stack data team (warehouse plus dbt plus Git) that must serve business colleagues with trusted numbers and now with AI answers.** Both vendors explicitly sell to that team, both sell to its consumers, and both are moving to code-backed, agent-built analytics. The differences are in the builder's starting job and the shape of the output.

| Dimension | Shared ground | Leans Hex | Leans Evidence |
| --- | --- | --- | --- |
| Buyer | Head of Data or analytics lead | Per-author seats; starts with a few analysts | Flat org fee or free Core; starts with an owner of reporting |
| Builder's first job | SQL on a cloud warehouse | Open-ended exploration, Python, ML, one-off investigations | Recurring reports and definitions maintained as code |
| Builder background | SQL, dbt, Snowflake | Data science, statistics, notebooks | Analytics engineering, software practice, Git |
| Consumer | CS, sales, finance, product, leadership | Operators who click through apps or chat in Threads | Readers of published reports, agent questions, scheduled PDFs |
| Deliverable | Shared metrics, dashboards, AI answers | Interactive apps, generated decks, actions (refund button, Slack alert) | Narrative reports, KPI pages, skills, embedded reports |
| Context layer | Semantic models, governed agent context | Context Studio, MetricFlow and Cube sync, evals | Version-controlled metrics, `agent/` context and skills |
| Embedded | Both gate it at Enterprise | Presigned iframe, attribute-filtered SQL | Backend session plus iframe, report-as-code releases |
| Not shared | | Python-heavy science, ML scoring, operational playbooks | Open-source self-hosting, research and release reporting (Every Cure), partner builds on Core |

**Verified vs inferred.** The rows on products, pricing, and integrations come from vendor docs and the vault notes. The "leans" columns are my inference from which workflows each vendor chooses to document and showcase; neither company discloses its customer mix. Hex's sample skews to US venture-backed tech; Evidence's named evidence is thinner and more varied (consumer software, research, partners), so the Evidence side of this table is less certain.

**Where they collide head-on:** EliseAI's CS team getting QBR material, Supabase's weekly metrics review, and Evidence's customer-health skill example are the same job (a data team packaging account or KPI analysis for operators). That shared job is the most useful comparison point for the interview.

## How each serves the overlap, and whether it delivers

**Short answer: Hex has more public proof that its output reaches operators and changes their work; Evidence has a sounder story for keeping that output correct and owned over time, but less public proof it gets used.** Neither has independent outcome evidence.

| Need of the overlapping customer | Hex | Evidence | Assessment |
| --- | --- | --- | --- |
| Answer a new question fast | Notebook plus agent plus Threads in one workspace | Studio agent over maintained reports and context | Both credible; Hex has more named usage claims (Notion, EliseAI) |
| Keep definitions consistent after changes | Semantic models, synced from dbt or Cube; reviews in product | Metrics and pages in Git with PR review and deploy previews | Evidence's model is more naturally reviewable; Hex's sync covers more external layers. Neither shows a measured drift reduction |
| Get the result into where work happens | Apps embedded in Salesforce and Notion; Slack alerts; generated decks; API actions | Email and Slack PDF schedules, exports, embedding, agent in Slack | Hex has more documented "last mile" cases; this is Evidence's weakest proven area in the notes too |
| Let non-technical people participate safely | Explorer seats, governed mode (guidance, not a security boundary), OAuth warehouse identity on Enterprise | Unlimited readers on Team, page grants, row rules on Enterprise | Hex gates control at Enterprise per seat; Evidence gates at Enterprise per org. Cost shape decides more deals than features here |
| Own the system and avoid lock-in | YAML export, 4.0 code files in private beta, no open-source runtime | Open-source Core, self-hosting, own GitHub repo | Clear Evidence advantage, valued mostly by engineering-minded teams |
| Deep analysis (Python, ML, forecasting) | Core strength (Kong forecasts, Ramp sentiment, Notion models) | Not the product's focus | Clear Hex advantage; Evidence should not chase it |

**Value gaps for each (inference):**

- **Hex:** per-editor pricing taxes wide authoring; customers still run Tableau or Amplitude beside it; governed mode is not enforcement; classic Git export is one-way, and 4.0 is beta. Apps built quickly by agents can sprawl, which Hex itself names as a 4.0 motivation ([new era post](https://hex.tech/blog/hex-new-era/)).
- **Evidence:** few named, current Studio customers with outcomes; delivery into operators' tools is less shown; the external-agent path tested in the homelab needed manual page handoff (F08 in [[Product Review Findings]]). Its maintained-as-code strength only pays off if teams actually revise and review, which is unmeasured.

**Implication for the review-bottleneck project:** Hex's own reason for 4.0 (agent-built work without provenance) is the same problem Sean described at Evidence. A reviewable, reproducible check on agent-made changes is not a niche concern; it is where both companies are heading.

## Durable trends vs fads

| Signal | Durable or fad? | Why |
| --- | --- | --- |
| Shared, maintained metric definitions | Durable | Same need since Looker's LookML; both vendors and dbt invest in it; AI raises the stakes because agents need it |
| Analytics defined as code and reviewed | Durable | Both now converge on files (Evidence from the start, Hex 4.0); it is what lets agents and humans edit safely |
| Getting analysis into operators' tools | Durable | Old BI complaint; Hex's best stories are about this, not about charts |
| External coding agents building analytics via MCP | Likely durable, details unsettled | Both ship MCP; Hex rebuilt its architecture for it. Tool scopes and save paths are still shifting month to month |
| "Chat replaces dashboards" | Partly fad | Customers still keep recurring dashboards (Supabase's 50, EliseAI's apps); chat adds a surface rather than replacing predictable pages |
| Headline outcome numbers (97%, 10x) | Marketing, not trend | Vendor-hosted, no method; useful only as evidence of which jobs customers value |
| Per-seat vs flat pricing | Open question | Agent usage makes "who is a seat" blurry; both now add AI credits, so cost shape is moving |

## Open questions and limits

- Neither company discloses customer mix by size, industry, or use case; every segment claim here is inferred from showcased stories.
- All Hex outcome figures are customer quotes on Hex's site. I found no independent case studies or recent practitioner threads in one search pass.
- I did not open job postings that name Hex, so builder backgrounds rest on customer-story titles.
- Hex's integrations page returned an error; integration claims come from the homepage and docs pages.
- The Evidence notes were not re-verified, and neither product was tested hands-on for this note.
- Good questions for Monday: which competitor shows up most in Evidence deals, and do they lose to Hex on exploration, on last-mile delivery, or on price shape?

## Sources

Hex, accessed 2026-11-02: [homepage](https://hex.tech/), [customers](https://hex.tech/customers/), [EliseAI](https://hex.tech/customers/eliseai/), [Supabase](https://hex.tech/customers/supabase/), [Ramp](https://hex.tech/customers/ramp/), [Notion](https://hex.tech/customers/notion/), [Inventa](https://hex.tech/customers/inventa/), [pricing](https://hex.tech/pricing/), [data connections](https://learn.hex.tech/docs/connect-to-data/data-connections/data-connections-introduction), [semantic models](https://learn.hex.tech/docs/connect-to-data/semantic-models/intro-to-semantic-models), [signed embedding](https://learn.hex.tech/docs/share-insights/embedding/signed-embedding), [A new era for Hex](https://hex.tech/blog/hex-new-era/), [dbt integration](https://docs.hex.tech/docs/connect-to-data/data-connections/dbt-integration) (search summary only). Evidence: [[Target Market and Customer Needs]], [[Customer Use Case Research]], and [[Hex vs Evidence - Product and Growth Research]], which carry their own citations.
