# Home Lab Analytics — review log

Started: 2026-10-31  
Review framework: [[Product Review Plan]]

## Walkthrough context

Build the Home Lab Analytics dashboard using Evidence and capture the experience as it happens. This is an exploratory personal use case; its relevance to major customer workflows is not yet established.

- **Project:** Home Lab Analytics.
- **Interface:** Evidence project with an AI sidebar, as reported by Sam; exact edition/version not yet recorded.
- **Goal:** A live dashboard showing various homelab analytics; Sam later clarified this will be the primary dashboard for homelab status, health, and loads.
- **Data source:** Existing homelab data stored in a Neon database. Sam reported adding a direct connector using the NeonDB owner account; no separate database user was created. The Studio agent reports successful inspection/querying, but this note-taking session has not independently verified the connection or data.
- **Current progress:** Sam reports publishing and is investigating GitHub version control, sharing, and maintenance by less technical collaborators. The specific published page/branch, GitHub connection, invitations, and sync behavior have not been tested here. The Claude/MCP comparison remains planned in [[Claude Dashboard Comparison Prompt]]; connection and Claude output have not been reported.
- **Refresh expectation:** Sam asked whether preview also refreshes every second or only after publishing. The latest supplied agent output refers to `auto_refresh: 1000`; earlier output referred to `60000`. The actual project configuration and preview/published behavior have not been inspected.
- **Still unspecified:** Final metric scope, acceptable source-data delay, and full completion criteria.

## Chronological notes

### 2026-10-31 — Starting the walkthrough

**Sam's words:**
> I am going to try to create the Home Lab Analytics dashboard using Evidence now.

**Type:** Session context; not a usability finding.

**Connection to the review:** This walkthrough can supply evidence for [[Product Review Plan#Q1 — Why choose Evidence?|Q1: Evidence's value]] and [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability]]. Connect observations about Studio, sharing, reuse, or permissions to the corresponding questions when they arise.

**Interpretation:** The hands-on review is beginning. No conclusions about product quality or customer fit follow from this starting note.

### 2026-10-31 — Project created; first prompt submitted to the AI sidebar

**Sam's words:**
> I basically just created a project called Home Lab Analytics, and there's an AI thing on the side. So I am just putting—I put in the prompt above, and let's see what happens.

**Dashboard prompt:**
> i want to create a live dashboard that shows various analytics from my homelab. i have the data being stored in a neon db. help me create a dashboard.

**Type:** Workflow observation; outcome pending.

**Context and outcome:** Sam created the project and submitted a broad, plain-language dashboard request through the AI sidebar. The data already exists in Neon. No AI response, connection result, generated dashboard, frustration, or successful completion has been reported yet.

**Connection to the review:**
- [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability]] — How effectively does the AI turn this initial request into understandable next steps? Does it clarify the data connection, useful metrics, and what "live" should mean?
- [[Product Review Plan#Q1 — Why choose Evidence?|Q1: Evidence's value]] and [[Product Review Plan#Q6 — Where do alternatives provide more value?|Q6: alternatives]] — This is a concrete starting point for comparing an Evidence-assisted build with giving the same request to a general AI coding tool.
- [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: Studio's additional value]] — If this is Studio, the integrated AI workflow is a candidate benefit to evaluate; its advantage over an open-source workflow is not established yet.

**Interpretation / follow-up:** The next useful evidence is the AI's response and Sam's experience following it. "Live" creates an expectation to examine later: whether the resulting dashboard updates as needed and whether its refresh behavior is clear. No refresh capability or limitation has been demonstrated yet.

### HLA-01 — Leaving the project separates setup from the agent; entered details are lost

Date: 2026-10-31. Entries HLA-01 through HLA-08 come from this dictated update. Related points are grouped; HLA-07 was reported immediately after the agent response in HLA-05.

**Sam's words:**
> So the agent told me that, like, I should go to this other page, the Connectors page, and connect my Neon database since it's not connected yet before it can make me a dashboard, and gave me some instructions. But I had to go out of the project I just created to get there, like the page it told me to go to. But now the agent isn't there with me. So, like, if I wanted to talk to the agent back that I forgot something, I would have to go all the way back into my project and then go here. So that one's a bit, like, frustrating there.
>
> So I did have to go out of the connection page to, like, look at the agent again. But then when I came back, all the information that I did have was wiped. Now I'm, like, wondering if the agent could just do these things for me and ask me for it.

**Observed sequence:** Agent directs Sam to database setup → Sam leaves the project → agent is unavailable there → Sam returns to consult it → on returning to connection setup, previously entered information is gone. Exact fields and whether a save action was available are not recorded.

**Impact:** Reported frustration, backtracking, and loss of entered setup information. No database data loss was reported.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integrated experience]]. Related to the earlier expectation of integrated help in [[Product Feedback Notes]].

**Interpretation / candidate improvements:** Guidance is separated from the task it supports. Consider keeping the agent accessible during setup or preserving the connection draft across navigation. Sam also proposes guided setup through the agent. These are candidate solutions, not confirmed missing capabilities.

### HLA-02 — A connector link exists, but clicking it does not navigate

**Sam's words, in sequence:**
> And maybe, like, in the agent, it should just give me, like a clickable button to get me to this page directly instead of me having to find this, so I don't go to the wrong page by accident.
>
> So the agent actually did give me a clickable link as a response to the prompt with the connections page, but the connections page doesn't even work. Like when I click it, it doesn't actually take me to anything. It just stays on the page I'm on.

**Observation:** The later statement corrects the initial impression that no direct navigation was offered. A link was present; Sam reports no navigation when clicking it. The target URL and failure cause are not recorded. This does not establish that the entire Connectors page is broken.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integrated experience]]. Related to [[#HLA-01 — Leaving the project separates setup from the agent; entered details are lost|HLA-01]]: reliable navigation would reduce page-finding effort, while access to help and preservation of entered details are separate concerns.

**Interpretation:** The useful recommendation is to make the existing action work, rather than conclude that a navigation feature must be added. Reproduction remains unconfirmed.

### HLA-03 — Team invitation is discoverable; role meanings require investigation

**Sam's words:**
> It prompted me to, like, there's just, like, an invite team member thing that just showed up on the screen where I can, like, select what project to go into when I came out of the connections. When I clicked that, it took me to the team member, like, team setting. It opened, uh, yeah, and here I can, like, add team members, and there's various roles. I can do viewer, org viewer, developer, and admin. I'll probably need to look at some docs to understand what each of these roles are.

**Observation:** Sam found an invitation entry point and reached team settings. Reported role labels: viewer, org viewer, developer, admin. No invitation was reported sent. Role scope, permissions, and any explanatory text have not been verified.

**Connections:** [[Product Review Plan#Q3 — How well does collaboration work?|Q3: collaboration and permissions]]; [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability]].

**Interpretation / follow-up:** Positive discovery of a collaboration workflow, with uncertainty about role selection. Investigate whether the interface explains role differences—especially viewer versus org viewer—and the project/organization scope before inviting someone. Do not infer permission granularity from labels alone.

### HLA-04 — Sync schedule guidance leads to navigation and documentation uncertainty

**Sam's words:**
> It told me if I want, like, a live fuel, I need to pick the shortest interval the connector allows. But I only... I'll have to go back to the screen to really know, like, probably how to do that, set a schedule. It didn't really tell me how to set a schedule.
>
> Still trying to figure out how to make a sync schedule. In the doc, it says I need to go to the sources page, but I can't easily find that.

**Prompt to the agent:**
> how do i set a sync schedeule

**Observation:** The initial guidance referred to choosing the shortest allowed interval without making the scheduling steps clear to Sam. Documentation referred to a Sources page Sam could not easily locate.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability and documentation]]; [[Product Review Plan#Q1 — Why choose Evidence?|Q1: fit for the desired live dashboard]].

**Interpretation / follow-up:** The difficulty spans agent instructions, documentation terminology, and navigation. Possible edition/version or connector differences are unconfirmed. Record the actual refresh requirement before judging suitability; no minimum sync interval has been established.

### HLA-05 — Agent changes its recommendation; connector choice remains unclear

**Agent response supplied by Sam:**

The following is a transcript of the other agent's output, with formatting normalized. It is evidence of guidance Sam received, not independently verified technical advice.

> I need to correct my earlier answer. **You probably don't need a sync schedule.** For a live homelab dashboard, use the **direct Postgres connector** instead. The docs say it works with Neon.
>
> **Direct connector (recommended)**
>
> - Evidence queries your Neon database each time the dashboard loads or a filter changes, so there's no sync delay and no schedule to set.
> - Go to **Connectors** in the sidebar and choose **Postgres** in the **Warehouse** card.
> - Fill in host, port (5432), database, user and password.
>   - Enter the hostname only, not a `postgres://` URL.
>   - Leave SSL mode on the default, **Verify full**. Neon's certificates work with it.
> - Click **Test Connection**, then **Save**.
> - If your tables aren't in `public`, set **Schema**, or write `schema.table` in your queries.
> - Use Neon's direct endpoint, not the pooled one, if you run into schema or timeout oddities.
> - Create a read-only role for Evidence:
>
> ```sql
> CREATE ROLE evidence LOGIN PASSWORD '<strong-password>';
> GRANT CONNECT ON DATABASE <your_db> TO evidence;
> GRANT USAGE ON SCHEMA public TO evidence;
> GRANT SELECT ON ALL TABLES IN SCHEMA public TO evidence;
> ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON TABLES TO evidence;
> ```
>
> **Synced connector (only if you want a copy of the data)**
>
> - Add a **PostgreSQL** connector from **Connectors → New Connector**.
> - The steps are: fill in the connection details, select the schemas and tables to sync, then **configure your sync schedule**. That last step is where the schedule is set.
> - The docs don't say which intervals are offered, so I can't tell you the minimum. Data would only be as fresh as the last sync.
>
> If you want live data, use the direct connector. Neon's free tier may suspend the compute when it's idle, so the first load after a quiet period can be slow.
>
> Once it's saved, tell me and I'll look at your tables and build the dashboard.

**Sam's reaction and subsequent setup:**
> I didn't really understand from the output which option is better for me. I think I'm gonna go the synced connector route and see how that goes. I already added the first option. I didn't use, like, I didn't create, like, a new user or whatever on the Neon side. I just used, like, the NeonDB owner user to create that connector.

**Observation:** The agent explicitly corrected its earlier scheduling advice and recommended direct access. Despite that recommendation, Sam remained unsure which option best fit the goal and wanted to try the synced route. Sam had already added the direct connector using the existing NeonDB owner account instead of creating the suggested read-only role.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: decision support and onboarding]]; [[Product Review Plan#Q1 — Why choose Evidence?|Q1: workflow fit]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: value of integrated AI guidance]].

**Interpretation / follow-up:** A recommendation was present but did not resolve Sam's decision. Investigate whether the agent should first clarify acceptable data delay and expected refresh behavior, then explain the tradeoff in those terms. Querying on load/filter changes, as claimed by the agent, does not itself establish that an already-open dashboard updates automatically. Actual behavior remains untested. The account choice is setup context; its effective permissions have not been assessed, and no database changes were performed by this note-taking session.

### HLA-06 — Documentation describes navigation Sam cannot find

**Sam's words:**
> I don't see a connection connectors page. Even in the docs, it tells me that to bow into open the connectors page, go to connectors in the sidebar in the warehouse card at the top, select Snowflake. But, like, there's no really connectors in the sidebar.

**Observation:** Sam reports that the documented Connectors sidebar entry and Warehouse-card path do not match the navigation they can locate. Documentation described selecting Snowflake while the task involves Neon/Postgres. The exact documentation page, interface version, and reason for the mismatch are not yet recorded.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: documentation and navigation]]. Related to [[#HLA-04 — Sync schedule guidance leads to navigation and documentation uncertainty|HLA-04]] and [[#HLA-02 — A connector link exists, but clicking it does not navigate|HLA-02]].

**Interpretation:** Multiple routes to setup—agent instructions, a clickable link, and documentation—have not reliably guided Sam to the intended place. This supports investigating consistency across help and interface terminology; it does not establish that a connector capability is absent.

### HLA-07 — No copy button noticed beneath the agent response

**Sam's words:**
> There's no copy button at the bottom.

**Observation:** Sam did not find a copy button beneath the response. The response included connection instructions and SQL. What Sam wanted to copy, and whether copying is available elsewhere, were not specified.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability]].

**Interpretation / follow-up:** A potential interaction improvement for transferring instructions or code. No blocked task or broader absence of copy functionality has been established. This was reported immediately after the agent response; grouped separately here for clarity.

### HLA-08 — Asking about the synced connector is followed by a dashboard build

**Prompt to the agent:**
> i added the direct connector and cannot find hwo to do the synced connector

**Sam's words:**
> It just started building the dashboard now.

**Observation:** Sam asked how to find/add the synced connector after adding the direct connector. Sam reports that the agent then began building the dashboard. No answer resolving the connector question was reported.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: intent handling and user control]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integrated AI workflow]].

**Interpretation / follow-up:** Possible mismatch between the immediate question and the agent's next action. The earlier agent response had offered to build once a connector was saved, which may be relevant, but its actual reasoning is unknown. Record whether the build eventually addresses the question, which connector it uses, and whether the resulting dashboard meets Sam's needs. Build success and dashboard quality are not yet known.

**Later update:** In [[#HLA-09 — Agent reports a completed dashboard and explains the direct-connector choice|HLA-09]], the agent says the dashboard is built, identifies the direct connector, and explains why it considers syncing unnecessary. Sam then reports accepting the page in [[#HLA-10 — Data-based suggestions are welcome; Sam accepts the staged page|HLA-10]]. This adds the subsequent outcome without removing the earlier mismatch between the question and the action.

### HLA-09 — Agent reports a completed dashboard and explains the direct-connector choice

Date: 2026-10-31.

**Agent response supplied by Sam:**

The following is the other agent's output, with formatting normalized. Its technical claims and data interpretations have not been independently verified.

> The dashboard is built and showing your live Neon data on a new page, `pages/homelab`. It's staged, so click **Accept** to save it.
>
> **You don't need the synced connector.** Your direct connector is already working, and the dashboard queries Neon every time the page loads. The page also sets `auto_refresh: 60000`, so it re-runs its queries every minute. If you'd like a different interval, change that number (it's in milliseconds).
>
> **What's on the page**
>
> - **KPI row:** Nodes Online (5), Avg CPU (3.0%), Cluster Memory Used (38.3%) and Data Age in minutes.
> - **CPU Utilization by Node:** last 24 hours, averaged over 5-minute buckets, one line per node.
> - **Memory Used by Node:** the same layout for memory.
> - **Node Status table:** role, freshness, CPU and memory bars, GiB used and total, and uptime.
>
> It reads from your `telemetry` schema. The KPIs and table use `latest_nodes`. The charts use `node_samples` joined to `nodes`.
>
> **Things I noticed**
>
> - **Data age:** Data Age shows about 14 minutes. The newest sample was collected at 22:35 UTC, so either your collector has paused or ingestion is lagging. The `pipeline_status` and `collector_cycles` tables would show why.
> - **Node A memory:** Node A is steady at about 85% memory, which is the highest in the cluster.
> - **Table totals:** the Total row at the bottom of the Node Status table sums the columns, so the CPU and memory totals aren't very meaningful. I can remove it if you like.
> - **Table access:** page components couldn't see the `telemetry` tables directly. That's why each chart and table reads from an inline SQL query instead.
>
> **Next steps I can add**
>
> - A node dropdown and a time-range selector (1h, 6h, 24h).
> - A pipeline health section covering collector cycle status, duration, missed deadlines and pending queue.
> - Uptime or "last reboot" tracking from `boot_time`, and threshold highlighting for CPU or memory above 80%.
>
> Tell me which of these you want.

**Observation:** The agent reports a completed, staged page, explains its connector choice and refresh configuration, describes the generated content, and proposes additions grounded in the available data. It also identifies potential data-freshness and aggregation issues in its own output.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: explanation and feedback]]; [[Product Review Plan#Q1 — Why choose Evidence?|Q1: reaching a useful result]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integrated authoring]]. Follow-up to [[#HLA-05 — Agent changes its recommendation; connector choice remains unclear|HLA-05]] and [[#HLA-08 — Asking about the synced connector is followed by a dashboard build|HLA-08]].

**Interpretation / follow-up:** The response now gives a concrete account of the chosen setup and claims automatic refresh, addressing part of the earlier uncertainty. Sam has not explicitly confirmed understanding the connector tradeoff. Refreshing the dashboard and receiving fresh source measurements are distinct: the reported 14-minute data age is a reason to evaluate end-to-end freshness, not proof of a dashboard-refresh failure. The reported meaningless totals and schema-access workaround are leads to inspect, not independently observed defects. The suspected collector/ingestion cause is the agent's hypothesis; no homelab diagnosis has been performed here.

### HLA-10 — Data-based suggestions are welcome; Sam accepts the staged page

Date: 2026-10-31.

**Sam's words:**
> i actually like how it is asking me by looking at my data what i could want to add in my dashboard. it is also asking me to accept changes for the page it added. i accepted and am gonna tell it now what i want it to add. gonna ask for options of types of things i could based on the data coming in.

**Type:** Positive usability observation; acceptance action; next-step intention.

**Observed / reported:** Sam explicitly likes that the agent looks at the available data and suggests possible dashboard additions. Sam reports accepting the staged page. The next intended action is to ask for more options based on the incoming data; the exact next prompt and result have not yet been supplied.

**Connections:**
- [[Product Review Plan#Q1 — Why choose Evidence?|Q1: Evidence's value]] — Candidate value extends beyond generating a requested chart: helping the user decide what would be useful to build from their data.
- [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integrated authoring]] and [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability]] — Suggestions tied to the current project/data were positively received and support iterative dashboard development.
- [[Product Review Plan#Q3 — How well does collaboration work?|Q3: review and revision]] — A staged change with an Accept action is a concrete review step to investigate. This observation establishes a single user's acceptance flow, not teammate review, role enforcement, or approval granularity.
- [[Product Review Plan#Q6 — Where do alternatives provide more value?|Q6: comparison]] — Test the effort needed to obtain similarly useful data-grounded suggestions with a general AI coding tool. This positive experience alone does not establish a unique Evidence capability.

**Interpretation / follow-up:** A useful positive finding: the agent helps Sam discover possibilities rather than requiring every metric and interaction to be specified upfront. The Accept step also provides an explicit decision before saving the generated page; Sam reported using it, but did not separately praise it or describe previewing a diff. Record whether subsequent suggestions remain relevant, explain their purpose, and translate into useful changes.

### HLA-11 — Recommendations connect the primary-dashboard goal to components and missing telemetry

Date: 2026-10-31.

**Sam's prompt:**
> based on the data coming in what kind of components would you suggest we add. this will be my priimary dashboard for seeing the status of my homelab its health loads.

**Agent response supplied by Sam:**

The following is the other agent's output, with formatting normalized. Data counts, interpretations, proposed thresholds, and technical claims are recorded as supplied, not independently verified or adopted as requirements.

> Here are my suggestions, based on what your collector records.
>
> **What the data covers**
>
> - **Nodes:** 5 expected nodes with a role each (GPU compute, general compute, monitoring parent, lightweight compute, storage host).
> - **Per-node readings:** CPU %, memory total/available/used, `boot_time`, uptime, and `scrape_success`. There are about 2,400 samples per node over the last 16 hours.
> - **Health fields:** `quality_status`, `freshness_status` and the age of each reading.
> - **Pipeline health:** `collector_cycles` has 980 cycles. Six of them are `degraded`, and the history includes up to 45 missed deadlines and up to 15 pending cycles.
> - **Not collected:** disk, network, temperature, containers and services. A dashboard built on this data can show whether your nodes are alive and loaded. It can't show whether your storage host is filling up.
>
> **Suggested components, in priority order**
>
> 1. **Status banner / KPI row.** This answers "is everything OK?" at a glance. Replace Avg CPU with "Nodes OK", "Nodes stale or degraded", "Pipeline state" and "Last data received". Colour them with the positive and negative theme colours.
> 2. **Node status cards or table with health flags.** One row per node, showing role, `freshness_status`, `quality_status`, current CPU, memory % and uptime. Flag any node over 85% memory or 90% CPU, or whose data is stale. This is the most useful section for a primary dashboard.
> 3. **Recent reboots and uptime.** Show `boot_time` per node. The data shows five distinct boot times, so something rebooted. Node B has been up since September 24, while the others rebooted around October 28. A "last reboot" column or a small timeline would make that easy to spot.
> 4. **Heatmap of CPU by node and hour.** This shows load patterns (nightly jobs, GPU runs) better than five overlapping lines. A 24-hour or 7-day heatmap, one row per node, works well.
> 5. **Memory pressure chart with `memory_available_gib`.** Available memory is more useful than used % for spotting trouble. Add a chart of available GiB per node, with a threshold line.
> 6. **Pipeline health section.** This covers collector cycle state over time, cycle duration, missed deadlines, pending queue size and `error_summary`. A dashboard is only trustworthy if its collector is. The 6 degraded cycles and the 45 missed deadlines are worth watching.
> 7. **Controls.** A node dropdown to focus on one host, a time-range selector (1h / 6h / 24h / 7d), and a toggle to compare the `live` and `budget` collection profiles.
>
> **Recommended layout**
>
> - **Row 1:** health banner and KPIs.
> - **Row 2:** the node status table.
> - **Row 3:** CPU heatmap next to the memory-available chart.
> - **Row 4:** reboot and uptime panel next to the pipeline health panel.
> - **Bottom:** the existing 24-hour CPU and memory trends, filtered by the controls.
>
> **Gaps worth fixing at the source** If this is your primary health dashboard, the biggest improvement is collecting more data. Disk usage (especially on the storage host), network throughput, temperatures (especially on the GPU node), and service or container up/down status would all be worth adding. Tell me when those land in Neon and I'll chart them.
>
> **What would you like me to build first?** I'd suggest items 1, 2 and 7, since they turn the page into an actual health view. I'd then add the pipeline health section.

**Sam's reaction and action:**
> i like this and am adding the sources it told me to

**Type:** Positive usability/value observation; clarified use case; reported source additions in progress.

**Observation:** Sam asked for component options for a primary health/status/load dashboard. The response organized its suggestions around the available data, gave priorities and a layout, and identified additional telemetry it said was needed. Sam explicitly liked the response and reports acting on the source recommendations. The specific sources selected, ingestion completion, and any requested component implementation have not been reported.

**Connections:**
- [[Product Review Plan#Q1 — Why choose Evidence?|Q1: Evidence's value]] — Reinforces [[#HLA-10 — Data-based suggestions are welcome; Sam accepts the staged page|HLA-10]]: helping decide what to build from the available data is valuable to Sam. The guidance now also influences what data to collect.
- [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integrated authoring]] and [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability]] — Prioritization, explanations, layout, and an explicit choice of next steps were positively received. This is evidence about perceived usefulness, not proof that every recommendation is accurate or implemented.
- [[Product Review Plan#Q5 — Which customer use cases matter most?|Q5: use-case definition]] — The personal walkthrough now has a clearer purpose: a primary view of homelab health, status, and load. Its relevance to major Evidence customer workflows is still unconfirmed.
- [[Product Review Plan#Q6 — Where do alternatives provide more value?|Q6: comparison]] — Compare the effort required for another tool or AI workflow to inspect the same data, explain its limits, and propose a useful prioritized dashboard.

**Interpretation / follow-up:** The response connects a broad goal to concrete components and explains where the input data limits coverage. Keep a source-data gap separate from an Evidence feature gap. Sam's willingness to add sources is a stronger signal of perceived usefulness than agreement alone; whether it improves the finished dashboard remains to be observed. Follow up on which telemetry arrives, whether the agent discovers it and updates its suggestions, and whether the primary dashboard becomes useful at a glance. The agent's specific claims about reboot history, sample coverage, thresholds, and health conditions remain unverified.

### HLA-12 — Components appear progressively in preview; Sam likes seeing the build happen

Date: 2026-10-31.

**Sam's words:**
> So I asked it to build the added components that it was suggesting before, one, two, three, and it said there's some weird thing happening with the Data Age component. So I said it just wants me to fix that. I was like sure. And it was really cool seeing all the things show up in the preview as it's writing it, which was pretty dope.

**Type:** Positive usability observation; implementation request; reported authorization of a fix.

**Observation:** Sam requested previously suggested components, referring to them as "one, two, three." The exact submitted prompt and mapping to the earlier numbered suggestions are not supplied, so the selected components are not inferred. The agent flagged a Data Age issue and Sam agreed to a fix; successful resolution has not been confirmed. Sam explicitly enjoyed watching components appear in preview while the agent wrote them.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: usability and progress visibility]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integrated authoring experience]]. Follows the suggestions and positive reaction in [[#HLA-11 — Recommendations connect the primary-dashboard goal to components and missing telemetry|HLA-11]].

**Interpretation:** Progressive preview gives Sam visible feedback during generation and is a positively received part of the experience. It is a concrete benefit to assess when comparing authoring workflows, rather than evidence that the generated components are correct. This observation does not establish simultaneous teammate collaboration.

### HLA-13 — Agent asks for acceptance while five errors remain visible

Date: 2026-10-31.

**Sam's words:**
> And I also see that there's like five errors of some sort on this page, and for some reason, it's not picking them up. I guess it's just telling me to accept, but at the top I can see that there's like five errors on this page. It's something to do with, like, the type being string instead of number or date for the max function or something.

**Type:** Reported validation/agent-awareness friction; exact diagnosis pending.

**Observation:** Sam sees an error indicator at the top of the page showing approximately five errors while the agent asks them to accept its changes. Sam's recollection concerns a string being supplied where a number or date is expected for a `max` function. This is an approximate description, not a captured error message. No screenshot, exact diagnostics, generated source, or agent completion response has been supplied.

**Impact:** Sam has to notice a discrepancy between the visible error state and the agent's apparent readiness for acceptance. The errors' effect on individual components and the rest of the dashboard is not yet known. Five diagnostics do not necessarily mean five independent defects.

**Connections:**
- [[Product Review Plan#Q4 — How usable is the workflow?|Q4: error handling, feedback, and recovery]] — Does the agent see and respond to the same errors the user sees? Does its completion message accurately describe unresolved problems?
- [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: value of integrated AI and validation]] — A candidate expectation of an integrated editor is that its agent can use available validation feedback before declaring a change ready.
- [[Product Review Plan#Q3 — How well does collaboration work?|Q3: review and publication confidence]] — The acceptance step from [[#HLA-10 — Data-based suggestions are welcome; Sam accepts the staged page|HLA-10]] now has a concrete question: how clearly are unresolved errors communicated at the point of review? This remains a single-user observation, not proof about publishing gates or teammate approvals.
- [[Product Review Plan#Q6 — Where do alternatives provide more value?|Q6: comparison]] — Compare how much manual checking is required to discover and resolve generated-code errors in an equivalent AI coding workflow.

**Interpretation / follow-up:** Possible gap between editor diagnostics and the agent's completion/repair loop. The evidence does not establish whether the agent lacks diagnostic access, overlooks feedback, or is affected by another issue. The agent did acknowledge a Data Age issue in [[#HLA-12 — Components appear progressively in preview; Sam likes seeing the build happen|HLA-12]], so avoid describing this as total lack of error awareness. It is not yet known whether the remaining errors share that cause or whether its attempted fix succeeded. Preserve exact messages and the later repair outcome when supplied. Candidate improvement: check available diagnostics and clearly surface any unresolved errors before requesting acceptance; whether acceptance should be blocked depends on error impact.

**Later update:** Sam found an editor action that sends a diagnostic into the agent chat ([[#HLA-15 — Diagnostic-to-chat action supplies a useful ready-made prompt|HLA-15]]). This establishes a manual handoff, not automatic agent access to all diagnostics. Later temperature-format output distinguishes warnings from errors ([[#HLA-18 — Warnings use the error prompt; agent reports a format fix without checking the render|HLA-18]]); it does not identify or independently verify resolution of the original `max`-related messages.

### HLA-14 — Preview versus published refresh behavior remains unclear

Date: 2026-10-31.

**Sam's question to the agent:**
> is the preview page also refreshed every second? or does that only happen after beign published?

**Agent response supplied by Sam:**

Transcript with formatting normalized; claims about documentation, configuration, and refresh behavior are not independently verified.

> The docs don't say. They describe `auto_refresh` as how often the page re-runs its queries, and they don't say whether that applies in the editor preview or only on a published page. I don't want to guess, but here's a quick way to find out.
>
> **Test it in the preview**
>
> 1. Watch the **Data Age (sec)** tile for about 10 seconds. If the page is refreshing, it should drop back toward 0–2 s every time a new reading arrives. If it only climbs, the preview isn't refreshing.
> 2. Also watch the Node A memory and CPU values, which change slightly as new readings arrive.
> 3. The CPU and memory charts and the pipeline charts only move about once a minute, so don't use them for this test.
>
> If the preview doesn't refresh, reload it manually to see current data. Then check the published page the same way.
>
> **Two things to know**
>
> - The preview may be intentionally slower or paused while you edit. I can't tell you which from the docs.
> - The reverse isn't a concern. A published page will use the `auto_refresh: 1000` setting in the frontmatter, and nothing else is needed to turn it on.
>
> Tell me what you see, and if the preview doesn't tick but you want to confirm the published behavior, I'll help you work out what to look for. The project-wide default also lives in `evidence.config.yaml` under `layout.auto_refresh`, but the page's own setting takes precedence.

**Observation:** Sam wants to know whether the editor preview behaves like the published dashboard at a one-second interval. The agent says the documentation does not establish preview behavior, proposes an observational test, and makes a more definite claim about publishing. Sam has not supplied the test outcome. The cited docs themselves were not supplied or checked in this note-taking session.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: preview clarity and documentation]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: authoring/publishing integration]]. Follows the refresh uncertainty in [[#HLA-09 — Agent reports a completed dashboard and explains the direct-connector choice|HLA-09]].

**Interpretation / follow-up:** A preview is less useful for assessing a live dashboard when its behavior relative to publishing is unclear. The proposed Data Age test is not conclusive by itself: a query can rerun while the source's newest measurement remains unchanged. Distinguish query refresh, arrival of fresh telemetry, and visible updates. The agent's preview-pausing explanation is speculation; its published-refresh assurance is unverified. No product limitation or documentation omission has been independently established.

### HLA-15 — Diagnostic-to-chat action supplies a useful ready-made prompt

Date: 2026-10-31.

**Sam's words:**
> When I hover over the error in the editor side, it gives you an option to send that error message into the chat where it will debug it and give you a reasoning behind it, which I really like because it makes it so much faster. And it doesn't just give it the error. It says, like a custom prompt: I'm seeing the following component error, line blah blah, please propose an edit as concisely as possible. And it's a pretty good prompt. I like that it just kind of does that for you.

**Type:** Positive usability observation; concrete error-recovery feature discovery.

**Observation:** Hovering over an editor diagnostic exposes an action to send its message and line reference to chat inside a prepared repair prompt. Sam explicitly likes the speed and the prompt being written for them, including the concise-edit instruction. This is more than a copy/paste convenience: it structures the next interaction.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: recovery and reduced effort]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: editor/agent integration]]. Refines [[#HLA-13 — Agent asks for acceptance while five errors remain visible|HLA-13]]: a manual route into debugging exists, while automatic diagnostic awareness remains unknown.

**Interpretation:** This is a concrete positively received integration benefit to compare with an external coding-agent workflow. Preserve the positive finding separately from the interruption side effect in [[#HLA-16 — Sending a diagnostic interrupts an existing component request|HLA-16]].

### HLA-16 — Sending a diagnostic interrupts an existing component request

Date: 2026-10-31.

**Sam's words:**
> Maybe there'd be a value in, like, adding it to a different agent that's just handling the errors instead of the one you're kind of talking to, so it doesn't interrupt. But, like, I don't know if that's, like, a big thing, but... I had a prompt going asking it to add components for temperature, but then I saw the error and I clicked the button where it let the error go into the chat. It actually interrupted my existing prompt, so it never actually did that.

**Observation:** During a temperature-component request, Sam clicked the diagnostic-to-chat action. Sam reports that this interrupted the active request and that it was not completed at that point. The original prompt, exact execution state, and whether the UI offered a warning, queue, or resumption action have not been supplied.

**Impact:** A convenient recovery action displaced work Sam already wanted done. Subsequent output discusses temperature-format edits, but does not establish that the original component request automatically resumed or was fully completed.

**Sam's proposed solution:** A separate agent for errors, offered tentatively rather than as a firm requirement.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: task continuity and user control]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integration quality]]. Related to [[#HLA-08 — Asking about the synced connector is followed by a dashboard build|HLA-08]]: the immediate interaction and intended task sequence can diverge, though a shared cause is not established.

**Interpretation / candidate improvements:** The underlying need is to handle a diagnostic without silently losing the active task. Queueing the repair, making interruption explicit, or offering reliable resumption are possible smaller solutions to evaluate alongside a separate agent. Do not assume multiple agents are necessary or supported.

### HLA-17 — Sam distinguishes framework skill from Studio workflow knowledge

Date: 2026-10-31.

**Sam's words, including their correction:**
> My thoughts on the AI agent that's in the Studio are, like, it's good. It's very good at Evidence. But I don't know how good it is at... No, let me scratch that. The agent is really good at using the Evidence framework. I don't know how good it is at Studio. I don't know if this is because the docs aren't updated, or it's not pulling in the docs for some reason. And I think the integration of the agent is a bit clunky, just because of the fix error thing. I think it to me feels like a less powerful model that's been fine-tuned really well at Evidence. So now I am gonna see if I can connect my own Codex to it and if that works.

**Type:** Overall user impression; hypotheses about cause; intended comparison.

**Observation:** Sam positively rates the agent's ability to use the Evidence framework while questioning its Studio navigation/workflow knowledge and integration. Sam plans to try their own Codex connection. No connection attempt or result has yet been reported.

**Connections:** [[Product Review Plan#Q1 — Why choose Evidence?|Q1: framework value]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: added Studio value]]; [[Product Review Plan#Q4 — How usable is the workflow?|Q4: end-to-end experience]]; [[Product Review Plan#Q6 — Where do alternatives provide more value?|Q6: comparison with an external agent]].

**Interpretation:** This is an emerging distinction supported by Sam's experiences: capability at generating framework content and quality of the surrounding application workflow should be evaluated separately. Outdated docs, failed retrieval, model strength, and fine-tuning are Sam's possible explanations, not established implementation facts. An external-agent comparison could help test what Studio contributes around the model; a preference alone would not identify the underlying cause.

### HLA-18 — Warnings use the error prompt; agent reports a format fix without checking the render

Date: 2026-10-31.

**Sam's words:**
> it sends warning and errors into the chat with the same default prompt

**Generated prompt and diagnostic supplied by Sam:**

Formatting normalized; the leading HTML space artifact is omitted.

> am seeing the following component error (line 250). Please propose an edit as concisely as possible:
>
> num0'°C' is not in the list of built-in formats. Consider checking the built-in list before using a custom format. Note that custom formats must follow Excel-style format codes.

**Supplied repair explanation:**
> The custom format has to be an Excel-style code, so `num0'°C'` becomes `0'°C'` and `num1'°C'` becomes `0.0'°C'`.

**Subsequent agent output supplied by Sam:**

These are the other agent's claims; no source or rendered view was inspected here.

> The page has no errors now. The editor still shows the "not in the list of built-in formats" notice on six lines. It's a warning, not an error, and it's expected.
>
> I changed `num0'°C'` to `0'°C'` and `num1'°C'` to `0.0'°C'`. Those are Excel-style codes with the degree sign as literal text. There's no built-in format for °C, so a custom code is the only way to show the unit. The warning is just a reminder to prefer built-ins when one exists.
>
> If you'd rather have no warnings, I can drop the `°C` suffix from the values and put the unit in each title, for example "Hottest CPU (°C)". I haven't looked at the rendered temperature section since this change.

**Observation:** Sam reports that warnings and errors share the same generated prompt, which calls the diagnostic a component error. The supplied message concerns a temperature format at line 250. The agent reports a change, zero errors, and six remaining warnings, and explicitly says it has not inspected the rendered temperature section. Sam has not independently confirmed those counts or the rendered result.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: diagnostic clarity and repair validation]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: agent/editor integration]]. Builds on the useful shortcut in [[#HLA-15 — Diagnostic-to-chat action supplies a useful ready-made prompt|HLA-15]] and the readiness question in [[#HLA-13 — Agent asks for acceptance while five errors remain visible|HLA-13]].

**Interpretation / follow-up:** Calling every diagnostic an error may obscure severity and encourage unnecessary repair work; preserve the actual diagnostic category in the generated prompt if available. The agent's explanation helps distinguish warnings from errors, but its claims about valid formats and expected warnings remain unverified. Zero reported errors and an uninspected render are separate facts; neither confirms visual correctness. These six temperature-format warnings must not be silently treated as the same messages as the earlier five `max`-related diagnostics. Record the render and final task outcome when supplied.

### HLA-19 — Studio agent explains what came from user instructions versus database discovery

Date: 2026-10-31.

**Studio agent retrospective supplied by Sam:**

Transcript with formatting normalized. This is the agent's account of its inputs and actions; it is not an independently audited conversation or query history.

> You gave me very little direct information. Most of what I built came from querying your Neon database, and the rest came from my own assumptions. Here is the split.
>
> **What you told me**
>
> 1. You wanted a live dashboard of homelab analytics, with the data stored in a Neon database.
> 2. Your connection is a direct Postgres connector. You added it yourself, and I never saw the credentials.
> 3. This would be your primary dashboard for homelab status, health and load. That led me to build the status banner, node grids and pipeline section.
> 4. You wanted it to update every second. You said you'd changed the collector to send to Neon more often.
> 5. You said you'd added new data, which turned out to be temperature, network, storage and service tables.
> 6. When I offered fixes and suggestions, you asked me to:
>    - fix the intro text and rebuild the Data Age tile
>    - build suggestions 1–3 (status banner, node health grids, pipeline health section)
> 7. You asked for temperature components "of whatever info is there".
> 8. You pasted three error messages, and I fixed each one.
>
> **What I found by querying Neon (you didn't tell me any of this)**
>
> - The data is in a `telemetry` schema with these tables:
>   - Node data: `nodes`, `latest_nodes`, `node_samples`, `node_current`
>   - Pipeline data: `collector_cycles`, `pipeline_status`
>   - Temperature data: `latest_temperatures`, `temperature_samples`
> - There are 5 nodes (Node A–E).
> - There are 8 temperature sensors: CPU package on all five nodes, ambient on Node C and Node D, and a GPU on Node A that reports `unsupported`.
> - Live node data updates every few seconds. Samples and collector cycles get one row a minute, and temperature readings arrive about every 12 seconds.

**Observation:** The retrospective distinguishes a small set of user goals from discovered data structure and agent assumptions. It also supplies additional reported history, including increased collector frequency, expanded data, three pasted error messages, and its interpretation of the selected components.

**Connections:** [[Product Review Plan#Q1 — Why choose Evidence?|Q1: value of data-aware generation]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integrated data context]]; [[Product Review Plan#Q6 — Where do alternatives provide more value?|Q6: establishing a comparison baseline]].

**Interpretation / limits:** Use the user-goal portion to seed the external-agent trial, while requiring fresh discovery of schema and readings. The statement that all three errors were fixed is the agent's claim, not rendered verification. Its statement about not seeing credentials has not been audited. The retrospective labels suggestions 1–3 as status banner, node grids, and pipeline health; this adds context to [[#HLA-12 — Components appear progressively in preview; Sam likes seeing the build happen|HLA-12]], but is not the same numbering as the earlier list in [[#HLA-11 — Recommendations connect the primary-dashboard goal to components and missing telemetry|HLA-11]]. Preserve both records rather than silently rewriting the earlier list.

### HLA-20 — Sam prepares a Claude/MCP build with minimal context on a separate page

Date: 2026-10-31.

**Sam's words:**
> The above is the information that I guess I gave the agent in Bill. But now I want to try it with Claude. So basically I'm going to connect the MCP for Evidence Studio to Claude, go through that, and kind of try to give it the similar information as above, right? So like I need you to first note down, like, my actions, what I'm doing and stuff here in my notes, but also give me, like, a prompt to give to Claude, giving it the minimal information that I gave their agent, and tell it to create a new page under Pages, but call it, like, Home Lab underscore Claude instead of Home Lab.md.

**Type:** Comparison setup and intended action; prompt prepared.

**Recorded plan:** Connect Claude to the Evidence Studio MCP, supply minimal user-provided context, and build a separate page named `Home Lab_Claude.md` under Pages. Preserve the existing dashboard for comparison. This is the latest specified external-agent trial, following the earlier Codex intention in [[#HLA-17 — Sam distinguishes framework skill from Studio workflow knowledge|HLA-17]]. No completed connection or Claude run has been reported.

**Artifact:** [[Claude Dashboard Comparison Prompt]]. It includes the Neon/direct-connector setup, primary status/health/load goal, one-second refresh request, increased collection frequency, recently added data, and requested component categories. It omits discovered tables, node/sensor details, observed cadences, previous errors, and fixes. It asks Claude to inspect the data independently and avoid reading/copying the original dashboard.

**Connections:** [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: native agent's added value]]; [[Product Review Plan#Q4 — How usable is the workflow?|Q4: setup and authoring experience]]; [[Product Review Plan#Q6 — Where do alternatives provide more value?|Q6: alternative agent workflow]].

**Interpretation / comparison limits:** This tests Claude through MCP versus the native Studio agent while retaining Evidence as the platform. It does not compare Evidence with a standalone AI-built app, and differences may reflect tooling, context, permissions, or model behavior. The prompt consolidates goals from several original turns, and data coverage/cadence may have changed; it is not an identical replay. Record setup effort, available tools, exact model if known, discovery quality, interventions, diagnostics, validation, and the useful result. The prepared prompt does not prove MCP supports any particular action; Claude must determine what its connected tools can do.

### HLA-21 — After publishing, Sam asks how to own the repo and share maintenance

Date: 2026-10-31.

**Sam's prompt to the Studio agent:**
> so i published where can i now version control everything and see in my github and share with other people so they can also maintain stuff?

**Studio agent response supplied by Sam:**

The same exchange was pasted twice in this update; it is captured once here, not counted as two separate interactions. Formatting normalized. This transcript records the guidance received; only the specific documentation findings in HLA-23 below were checked independently.

> Your project is stored as a Git repository. Right now it's in Evidence's managed repo, which you can only edit from Studio. To see it in GitHub and share it, link the project to your own GitHub repo.
>
> **Link the project to GitHub**
>
> 1. Go to [Organization Settings](https://evidence.studio/settings/organization) and connect your GitHub account. You can allow all repositories or only specific ones.
> 2. Create an empty repo on GitHub first. The repo must already exist, because Studio can't create one.
> 3. Open the project, click the cog icon next to the project name in the sidebar, then open project settings.
> 4. Under **Version Control**, check **Connect to GitHub repository** and choose:
>    - the repo
>    - the published branch, usually `main`
>    - the project root: the default is `pages`, or leave it blank to store files at the repo root
> 5. Click **Save**. Nothing is synced yet at this point.
> 6. Go back to the editor and click **Publish**. That pushes the current project to GitHub.
>
> **What ends up in the repo**
>
> - Pages, including `pages/homelab` with its SQL queries
> - Partials and SQL files
> - `theme.yaml` and `evidence.config.yaml`
> - Page settings, such as `auto_refresh`, which live in the page's frontmatter
> - `access.yaml`, if you use page-level access, and `translations.yaml`
>
> **What stays outside Git**
>
> - The docs list logo, organization theme, decimal separators and the custom AI prompt as organization-wide settings edited in Studio.
> - Data connections aren't on the version-controlled list. I'd assume your Neon credentials stay in Studio and don't go to GitHub, but I haven't confirmed that. Check the repo after the first publish before making it public.
>
> **Letting others maintain it**
>
> - Give people access to the GitHub repo, and add them to your Evidence organization so they can use Studio.
> - Others can edit in Studio or locally with the [CLI](https://www.evidence.studio/homelab-analytics/main/pages/homelab/edit?linkPreviewPath=cli), and the two stay in sync through Git.
> - **Main only:** every Publish pushes straight to `main` and goes live. This suits one person.
> - **Feature branches (better for a team):** developers use **Commit** on a branch. Publish merges into the published branch with a squash commit, or you can open a pull request on GitHub and review it there.
> - Studio edits are shared before they're committed. If two people open the same file, they see each other's uncommitted changes.
>
> If you use a team workflow, I'd suggest feature branches and PRs, since this is the dashboard you rely on for your homelab's health.

**Observation:** Sam reports reaching publication and now wants external version history and shared maintenance. This moves the walkthrough into the share/review/maintain stages of the review plan. No GitHub repository, connector migration, invitation, or teammate edit is reported completed. The agent's credential-handling assumption remains unverified, and the supplied CLI link's behavior was not tested.

**Connections:** [[Product Review Plan#Q3 — How well does collaboration work?|Q3: sharing, review, maintenance, and permissions]]; [[Product Review Plan#Q1 — Why choose Evidence?|Q1: maintainable reporting]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: managed development workflow]]; [[Product Review Plan#Q4 — How usable is the workflow?|Q4: onboarding and discoverability]].

**Interpretation:** Getting to a published report has not made the ownership/collaboration model self-explanatory. The response mixes organization membership, GitHub permissions, draft sharing, commits, and deployment. These are distinct tasks; explanations should start from what the collaborator needs to do. This is a usability question, not evidence that Git integration is absent or broken.

### HLA-22 — Sam wants voice-to-text input in the Studio agent

Date: 2026-10-31.

**Sam's words:**
> also it would be nice to have voice to text feature in the agent.

**Type:** Feature request / input preference.

**Connections:** [[Product Review Plan#Q4 — How usable is the workflow?|Q4: ease of expressing requests]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: integrated agent experience]].

**Interpretation:** Sam would value dictating requests directly into the agent. Record this as a requested interaction rather than assume all forms of dictation are unavailable. Native Studio support, browser/OS dictation behavior, and the impact on task completion were not investigated.

### HLA-23 — Can a less technical collaborator maintain this without learning the whole Git workflow?

Date: 2026-10-31.

**Sam's words:**
> Would people who are not super tech savvy and can, like, are not super technical, be able to do all this stuff? What kind of collaboration is even... is this letting? Like, okay, so you would need to give people access to my repo, the GitHub repo, add them to Evidence organization so they can use Studio. How does the syncing work between the repo and Studio?

**Type:** Open usability/product-positioning question; request for clarification.

**Documentation check, 2026-10-31:**

- GitHub is optional: projects have an Evidence-managed repo by default. Studio drafts are shared before commit. Linking an external repo requires a first Publish to populate it; later changes flow through Git. [Version Control](https://docs.evidence.dev/features/version-control)
- A push/PR merge into the published branch triggers publishing. Roles distinguish report readers (Viewer/Org Viewer) from editors (Developer) and organization administrators (Admin). [Publishing](https://docs.evidence.dev/publishing)
- Developer/Admin/Org Viewer can view all pages regardless of page grants; page-level access is a reader-permission model, not demonstrated page-scoped editing. [Page Level Access Control](https://docs.evidence.dev/features/page-level-access-control)
- Studio provides agent-generated edits in a diff that users can accept/reject. This documents assistance for editing, not proof a novice can confidently maintain the result. [Editing](https://docs.evidence.dev/editing)
- GitHub PR previews let reviewers inspect a proposed report before merge. [Deploy Previews](https://evidence.dev/blog/deploy-previews)

These are current documentation claims, not an end-to-end test of Sam's project. In particular, whether every Studio-only editor on a GitHub-connected project needs an individual GitHub invitation was not explicitly established by the checked docs. Do not treat the other agent's instruction to invite everyone to both systems as a universal prerequisite; collaboration in a managed-repo project does not require moving to GitHub.

**Connections:** [[Product Review Plan#Q3 — How well does collaboration work?|Q3: collaborator journeys and permission scope]]; [[Product Review Plan#Q4 — How usable is the workflow?|Q4: technical burden]]; [[Product Review Plan#Q2 — Why choose Studio over open source?|Q2: value of abstracting development operations]].

**Interpretation:** The collaboration model supports report consumption, shared authoring, and software-style review/release workflows. The unanswered product question is how much of that machinery a nontechnical maintainer must understand. The agent could distinguish a reader invitation, Studio editing, and direct GitHub/local maintenance before explaining setup.

**Proposed follow-up test, not yet run:** Invite an authorized test participant with little Git experience. Ask them to change one label and add one metric using the Studio agent, explain the proposed change, request review, and identify when it becomes live. Record GitHub/account requirements, role clarity, help visits, terminology confusion, and whether they can finish without author intervention. Test simultaneous Studio drafts and conflicting external changes separately; timing and conflict behavior are not specified well enough by the checked docs to promise automatic conflict-free synchronization.

## Emerging patterns

- **Help is separated from setup.** [[#HLA-01 — Leaving the project separates setup from the agent; entered details are lost|HLA-01]] connects to the earlier Docs-button expectation in [[Product Feedback Notes]]. The new observation includes lost entered details, making the navigation cost more concrete.
- **Instructions and navigation are not lining up for Sam.** [[#HLA-02 — A connector link exists, but clicking it does not navigate|HLA-02]], [[#HLA-04 — Sync schedule guidance leads to navigation and documentation uncertainty|HLA-04]], and [[#HLA-06 — Documentation describes navigation Sam cannot find|HLA-06]] provide related observations; a shared cause is not established.
- **Connector guidance became concrete after the build.** Selection remained unclear after the corrected recommendation ([[#HLA-05 — Agent changes its recommendation; connector choice remains unclear|HLA-05]]), followed by a build while the immediate question was unresolved ([[#HLA-08 — Asking about the synced connector is followed by a dashboard build|HLA-08]]). The completion response subsequently explains direct access and claims automatic refresh ([[#HLA-09 — Agent reports a completed dashboard and explains the direct-connector choice|HLA-09]]). Sam accepted the page; understanding of the tradeoff and actual refresh behavior remain unconfirmed.
- **Collaboration has a concrete entry point to evaluate.** Team settings exposed four reported roles, but Sam does not yet understand their scope ([[#HLA-03 — Team invitation is discoverable; role meanings require investigation|HLA-03]]).
- **Publishing exposes a new collaboration-onboarding gap.** Sam wants GitHub ownership and shared maintenance ([[#HLA-21 — After publishing, Sam asks how to own the repo and share maintenance|HLA-21]]) but questions whether a less technical teammate can navigate the workflow ([[#HLA-23 — Can a less technical collaborator maintain this without learning the whole Git workflow?|HLA-23]]). Separate readers, Studio authors, and GitHub contributors when evaluating ease of collaboration.
- **Voice input is a requested improvement.** Sam would like voice-to-text in the agent ([[#HLA-22 — Sam wants voice-to-text input in the Studio agent|HLA-22]]); availability and impact are not yet tested.
- **Suggestions based on the user's data provide visible value.** Sam explicitly liked the initial suggestions ([[#HLA-10 — Data-based suggestions are welcome; Sam accepts the staged page|HLA-10]]), then asked for more and reports adding sources based on the recommendations ([[#HLA-11 — Recommendations connect the primary-dashboard goal to components and missing telemetry|HLA-11]]). This supports perceived usefulness across successive steps; accuracy, realized dashboard benefit, and advantage over alternatives remain to be tested.
- **Guidance extends from chart selection to data coverage.** The agent identified telemetry it said was missing for the stated primary-health-dashboard goal; Sam reports acting on that guidance ([[#HLA-11 — Recommendations connect the primary-dashboard goal to components and missing telemetry|HLA-11]]). Distinguish limits in the collected data from limits in the product's charting or monitoring capabilities.
- **Generated changes have an explicit acceptance step.** Sam reports accepting the staged page ([[#HLA-10 — Data-based suggestions are welcome; Sam accepts the staged page|HLA-10]]). Inspect preview, revision, and teammate-review behavior separately before drawing broader collaboration conclusions.
- **Progressive preview is enjoyable, but readiness needs separate validation.** Sam likes seeing components appear as they are written ([[#HLA-12 — Components appear progressively in preview; Sam likes seeing the build happen|HLA-12]]), while visible errors remain at the point of requested acceptance ([[#HLA-13 — Agent asks for acceptance while five errors remain visible|HLA-13]]). The positive preview experience and validation concern should both be preserved in the review.
- **The diagnostic shortcut saves effort but can disrupt task continuity.** Sam likes the prepared repair prompt ([[#HLA-15 — Diagnostic-to-chat action supplies a useful ready-made prompt|HLA-15]]), yet reports it interrupting an active component request ([[#HLA-16 — Sending a diagnostic interrupts an existing component request|HLA-16]]). Warnings also receive the error wording ([[#HLA-18 — Warnings use the error prompt; agent reports a format fix without checking the render|HLA-18]]).
- **Framework skill and Studio integration are separate evaluation dimensions.** Sam explicitly distinguishes the two and plans to try an external Codex connection ([[#HLA-17 — Sam distinguishes framework skill from Studio workflow knowledge|HLA-17]]). The perceived cause is not yet established.
- **The external-agent comparison is now concrete.** Sam's latest plan is Claude through the Studio MCP with minimal goals and a separate page ([[#HLA-20 — Sam prepares a Claude/MCP build with minimal context on a separate page|HLA-20]]). The Studio agent's discovery retrospective supplies a baseline ([[#HLA-19 — Studio agent explains what came from user instructions versus database discovery|HLA-19]]); no comparison result exists yet.
- **Preview and completion messages leave verification questions.** Preview refresh relative to publishing remains uncertain ([[#HLA-14 — Preview versus published refresh behavior remains unclear|HLA-14]]); a later repair response explicitly says the rendered section was not checked ([[#HLA-18 — Warnings use the error prompt; agent reports a format fix without checking the render|HLA-18]]).

Candidate priorities for investigation: task interruption during diagnostic handoff; visible diagnostics at requested acceptance and post-repair validation; loss of entered setup details; inaccessible help while configuring; navigation/help consistency; agent handling of clarification questions. These are provisional priorities within this walkthrough, not validated customer-wide severity ratings.

## How subsequent notes will be captured

Each dictated note gets a chronological entry with:
- **Sam's words:** the original observation, preserved separately from analysis.
- **Context and outcome:** task/step, expectation, actual behavior, impact, help used, and resolution, only where supplied.
- **Connection to the review:** links to the relevant review questions and related observations.
- **Interpretation / follow-up:** a clearly labeled inference or open question, where useful.

Capture frustrations, smooth interactions, questions, and workarounds. Keep later corrections and resolutions alongside the original experience rather than rewriting history.
