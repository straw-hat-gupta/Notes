Back to [Evidence Studio Feedback](Evidence%20Studio%20Feedback.md) · [Sources and references](References.md)

## Who I kept in mind

I kept two people in mind: the person maintaining reports, queries, and shared definitions, and the colleague using those reports to answer a business question. Evidence describes readers asking questions and saving shareable insights, with reports and project knowledge supplying context (["Analytics Agent"](https://evidence.dev/product/analytics-agent)). My reasoning is that reducing the maintainer's repeated work leaves more time to check what readers will see. I'm using my experience to put myself in these customers' shoes and better understand their needs.

The concrete task I chose is a data team maintaining guided account-health analysis for customer-success colleagues. Evidence describes an unnamed customer turning a complex health dashboard into a skill that asks relevant questions and guides the analysis. The original dashboard included product usage, support history, and renewal information; its growing set of inputs required knowledge of the customer's methodology ([McAskill, “That Dashboard”](https://evidence.dev/blog/that-dashboard-should-be-a-skill)).

In the scenario I pictured, the data team owns the method and its maintenance, while the customer-success colleague needs a relevant, explainable assessment. Those roles are my interpretation of the workflow. The maintainer's job is to keep the analysis correct as data and methods change, and explain a changed result to the colleague relying on it.

My homelab dashboard is a monitoring use case. What carries over is the developer experience of building, debugging, and revising a project over multiple sessions. I ended with a promising first dashboard I'd keep using and develop further. That experience helps me put myself in a report maintainer's shoes when thinking about setup, error fixes, and returning to unfinished work.

## Agent integration

**What prompted this:** Connecting Neon took me to a setup page outside the project, where the agent chat wasn't available. Sending an error to chat then interrupted a request to add temperature components, which I had to request again. Later, after reopening Studio, a listed conversation returned “chat not found” (walkthrough steps 2, 4, and 9). My guess is that the interface separates report work from setup in a way that made those transitions harder; I haven't inspected the implementation.

**What I'd keep:** the visible code and the ability to shape the agent through version-controlled context and skills. I noticed `agent/` in the project but did not edit it. The docs describe always-loaded context, on-demand skills, and CLI development with an agent of your choice (["Evidence Agent"](https://docs.evidence.dev/features/evidence-agent); ["CLI"](https://docs.evidence.dev/cli)).

**What I'd explore:** the agent helping carry out Studio workflows, including connection and team setup within my permissions, while retaining the conversation and task. One possible interface is an Agent View and Studio's existing IDE view, with the same conversation and task carried between them. The agent can already adjust project and page settings; this wish concerns carrying help across the surrounding workflow (["Editing"](https://docs.evidence.dev/editing)).

**What already exists:** The published Analytics Agent can answer questions about data and existing reports, show charts and tables in chat, and build standalone insights with written findings and visualizations. Users can refine an insight draft and save it as its own report in their library. The agent uses project context and skills, and insights retain their prompt and implementation notes (["Analytics Agent"](https://evidence.dev/product/analytics-agent); ["Evidence Agent"](https://docs.evidence.dev/features/evidence-agent)). In the IDE view, the Studio agent can query connected data, inspect visualizations, and edit pages and settings (["Editing"](https://docs.evidence.dev/editing)). Saved insight content can also be reused in maintained pages.

In the published project, I liked the choice between a full-page chat and a small popup at the bottom, with charts and tables shown in the conversation. It makes questions easier to explore while keeping the report close by. I especially like saved insights because readers can keep several useful analyses about a report and return to them later. I see the Agent View as a way to connect that existing analytical experience more closely to project setup and authoring.

**My question:** Could an Agent View make the existing agent a conversational way to develop a project, alongside the existing IDE view? A user could discuss the report or reusable analytical workflow they want, and have the agent help set up the project and its pages, skills, and other contents. They could explore connected data, inspect individual components, ask follow-up questions, and add selected components to a report or dashboard, keeping the same conversation when they switch to the IDE. This would build on the Analytics Agent's existing insights.

For a data team, I think this could make it easier to turn an exploratory conversation into a reusable report or workflow for colleagues. The IDE view would keep the files, queries, and implementation visible when the maintainer is ready to inspect or change them.

For a maintainer, that could reduce re-explaining and backtracking without hiding the code they need to review. Seeing the files alongside the same conversation might also help someone learn the framework and understand how a maintained project is organized. That could give technical and less technical colleagues a shared reference when discussing changes.

**Where I'd start:** guided connection setup alongside the same agent, an error fix that retains the original request, and reliable reopening of chats shown in the list. Broader workflow actions and an Agent View sharing its conversation with the existing IDE view are directions to explore from that starting point. These observations identify related user costs, not a proven common technical cause.

**How I'd know:** a user can complete connection setup, handle an error fix, and return to a task without repeating instructions to the agent. Completion time and the number of repeated requests would help show whether this saves effort. Time recovered here can go toward reviewing the report colleagues will use. This workflow integration and continuity is my main recommendation, supported by clear information about which checks the agent ran on its report edits.

## What the agent did and checked

**What prompted this:** I accepted changes with about five errors visible, and a separate response about an error fix said the rendered section had not been inspected (step 4). Claude used Studio MCP's visualize tool to render and check its page before handoff (["Studio MCP"](https://docs.evidence.dev/mcp/studio)); that was a useful contrast (step 6). The agent already shows a diff; what I wanted was clarity about checks and unfinished work.

**What already exists:** Evidence describes queries and sources behind answers, with the prompt and implementation notes saved alongside insights (["Analytics Agent"](https://evidence.dev/product/analytics-agent)). That is useful provenance; I did not test a complete record of agent actions during this walkthrough.

**What I'd like:** a concise completion note saying what changed, whether the agent checked for code errors and inspected the updated charts and tables, and what remains open. A record of queries, edits, and check results would help a user pick up the work later. This would help the maintainer review an agent-made change and answer a reader asking where a number came from. Keeping this record with the task would make unfinished work easier to pick up after an error fix or a return visit. I don't know whether the readiness mismatch came from unavailable diagnostics, missed feedback, or something else.

In the account-health scenario, a maintainer needs to distinguish a changed method from changed customer data when a colleague asks why an assessment moved. That is the practical value I see in keeping the change, its checks, and the sources understandable together.

**Where I'd start:** a completion note before Accept with three short parts: changed, checked, and still open. Could the Studio agent run a render check like the one available through MCP and report its result? I haven't established how the native agent accesses those tools. Preserve warning/error severity and name the checks actually run. A broader action history can build on that.

**How I'd know:** a user can tell which code and render checks ran, and what remains, without reconstructing the conversation. Successful rendering alone does not establish that the analysis is correct.

## A framework focused on BI

A big part of Evidence's appeal for me is having a framework and runtime organized around BI work. Core powers Studio, connects components to live warehouse queries, and supports reusable metrics. The component system provides reporting elements and validation; metric definitions can carry a shared calculation, filter, format, and label ([McAskill, “Evidence Core”](https://evidence.dev/blog/evidence-core); ["Components"](https://docs.evidence.dev/core-concepts/components); ["Metrics"](https://docs.evidence.dev/core-concepts/metrics)).

I like having that shared reporting structure built on familiar tools such as SQL and Markdown. It gives data teams and their agents common components, definitions, and conventions to work with. In the account-health scenario, the appeal is keeping the method and its reporting logic in a form the team can inspect and maintain.

The fit with a developer's existing workflow is another part of that value. Reports, metrics, and agent instructions can be version-controlled together. The documented CLI route supports local editing with an agent of your choice and pull requests with preview links (["Evidence Agent"](https://docs.evidence.dev/features/evidence-agent); ["CLI"](https://docs.evidence.dev/cli)). For teams already using Git, those are familiar ways to track, review, and maintain changes.

Studio's existing IDE view feels familiar too: files, code, preview, and an agent alongside the work. I liked being able to follow the Markdown and SQL while the dashboard was built. My Agent View proposal would add another way to work with that same project and conversation. The combination I value is a framework built for BI that fits the development practices a technical team already uses.

## Data scope

**My question:** which connections can this project and its agent use, and how do I make that scope explicit? The CLI docs describe using the organization's data connection; that does not establish every project's effective access (["Connect Your CLI to Your Data"](https://docs.evidence.dev/cli/connections)).

I'd prefer project-scoped connections and a visible choice of data for an investigation. For a data team serving several groups, I think that could make the intended scope easier to understand before sharing a report. Central connections may also save repeated administration; I haven't tested that tradeoff.

Choosing relevant data is different from enforcing who can access it. Evidence documents table/row controls and directs users of direct connectors to connector-specific rules (["Row Level Security"](https://docs.evidence.dev/features/row-level-security)). I did not test those controls or establish whether hosted project-specific connection configuration exists. This is a question and a preference, not a claim that the agent can query everything.

## Smaller wishes

**A copy button under agent responses.** I'd use it to move SQL or an explanation into a ticket or doc when discussing a report. This is a convenience wish, not a verified claim that no copy interaction exists.

**Voice input in the agent.** I'd use it to describe a report or investigation aloud. I used dictation for these notes. In my experience it is faster than typing and lets me express my thoughts more naturally.

The Docs and Support observations stay in the walkthrough rather than being repeated as additional wishes here.
