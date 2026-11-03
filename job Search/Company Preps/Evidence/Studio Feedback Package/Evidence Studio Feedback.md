**Time spent:** about 1.5 to 2 hours building and exploring, and 3 to 4 hours on research, analysis, and further exploration of the product.

**What I built:** A live homelab health dashboard with Neon db, using Studio's agent, with a separate Claude/MCP build, a second-account collaboration test, and GitHub setup.

I ended with a promising first dashboard I'd keep using and develop further. Building with the agent was the best part: suggestions came from my data, and I could follow the Markdown, SQL, and preview. The friction came during database setup, when an error fix interrupted my request, and when I couldn't reopen a previous Studio chat. My main wish is for the agent to work more directly with Studio's workflows, carrying the conversation and task through setup, error fixes, and return visits. When the agent changes a report, I'd like it to say which code errors it checked for, whether it inspected the updated charts and tables, and what still needs attention. That would help maintainers understand what has been verified before reviewing the result.

### Who I Had in Mind

I pictured a data team keeping an account-health assessment correct as data and methods change, then explaining a changed result to customer-success colleagues. Evidence's account-health skill story informed that scenario; the roles are my interpretation ([McAskill, “That Dashboard”](https://evidence.dev/blog/that-dashboard-should-be-a-skill)).

My homelab dashboard is a monitoring use case, which is different from the business-reporting scenario above. What carries over is the developer experience of building, debugging, and revising a project over multiple sessions. I'm using that experience to put myself in the customer's shoes and better understand what they need.

### My Feedback

**1. An agent that’s integrated with Studio and keeps the task.** Connecting Neon took me to a setup page outside the project, where I couldn't access the agent chat. Sending an error to chat interrupted a request to add temperature components, so I had to ask for them again. After closing and reopening Studio, a previous conversation was still listed but returned “chat not found” (steps 2, 4, and 9). I'd like the agent to help carry out Studio workflows, including connection and team setup within my permissions, while retaining the task and conversation. The agent can already adjust project and page settings (["Editing"](https://docs.evidence.dev/editing)); extending that help to connection setup could let users finish more of the workflow without switching between setup pages and the project chat.

I'd start with a guided connection setup alongside the same agent, error fixes that don't interrupt the original request, and reliable reopening of listed chats. Those would reduce backtracking for a maintainer preparing reports for others. A larger direction I'd explore is an Agent View alongside Studio's existing IDE view, with the same conversation and task carried between them. I'd judge the improvement by whether a user can complete connection setup or resume an interrupted task without repeating instructions to the agent. Completion time and the number of repeated requests would be useful measures.

In the published project, I liked seeing charts and tables directly in the chat and choosing between a full-page chat and a small popup at the bottom. Insights can be refined and saved as standalone reports. I particularly like this because readers can keep and share useful analysis about a report and return to it later (["Analytics Agent"](https://evidence.dev/product/analytics-agent)).

Could an Agent View build on this for developing reports and dashboards? Users could set up a project, its pages and skills, and other project contents through the agent. They could also explore connected data, inspect individual components, ask follow-up questions about them, and add the ones they choose to a report. Keeping the conversation across the Agent and IDE views could help a data team move from an idea to a reusable report or workflow. [Agent integration](Analysis%20and%20Customer%20Reasoning.md#Agent%20integration)

**2. Knowing what changed and what was checked.** I accepted changes with about five errors showing; a separate response about an error fix said the rendered section hadn't been inspected (step 4). I appreciated that Claude used Studio MCP's visualize tool to render and check the page before handoff (step 6; ["Studio MCP"](https://docs.evidence.dev/mcp/studio)). Could the Studio agent run a similar check and say what it checked before Accept? The diff showed the edit. I also liked selecting a component to inspect its query results and SQL; that helped me understand the displayed numbers. Alongside those tools, I wanted to know what the agent itself had checked.

I'd add a brief completion note before Accept: what changed, what was checked, and what remains open. That supports the continuing workflow above: a maintainer returning to a report can see where to pick up and what still needs review. In the account-health scenario, that could help explain the basis of a changed assessment. I'd judge it by whether a user can tell which checks ran, including a render check of the updated charts and tables, without reconstructing the conversation. Rendering alone doesn't establish that the numbers are correct. [Checks and history](Analysis%20and%20Customer%20Reasoning.md#What%20the%20agent%20did%20and%20checked)

**3. A shared framework for BI.** A big part of Evidence's appeal for me is having a framework and runtime focused on BI, with queries, reusable metrics, components, and validation ([McAskill, “Evidence Core”](https://evidence.dev/blog/evidence-core)). That gives data teams and their agents a shared structure for building and maintaining reports. Keeping the code and queries visible was already useful in my build.

I also like how this fits into a developer's existing workflow. Reports, definitions, and agent instructions can live in Git, with local editing and pull-request review (["Evidence Agent"](https://docs.evidence.dev/features/evidence-agent); ["CLI"](https://docs.evidence.dev/cli)). For teams already using Git and an IDE, those are familiar ways to maintain a codebase. Studio's existing IDE view brings that familiarity into the browser. Together, the BI framework and development workflow are a big part of the value I see in Evidence. That's why I want the agent to stay connected to the task and be clear about its checks: it helps people build on that foundation with confidence. [Framework and developer workflow](Analysis%20and%20Customer%20Reasoning.md#A%20framework%20focused%20on%20BI)

### What I Did

**Step 1. Creating the project.** **Good:** A broad request started Home Lab Analytics. [Starting prompt](Walkthrough%20Details.md#1.%20Creating%20the%20project)

**Step 2. Connecting my database.** **Stuck:** Setup took me away from the agent; direct versus synced guidance and navigation confused me (Theme 1). [Connection walkthrough](Walkthrough%20Details.md#2.%20Connecting%20my%20database)

**Step 3. Building.** **Good:** Data-grounded suggestions prompted me to add telemetry; I watched queries and components appear. [Build sequence](Walkthrough%20Details.md#3.%20Building%20the%20report%20with%20the%20agent)

**Step 4. Fixing errors.** **Good:** Prepared prompts for error fixes. **Stuck:** An error fix interrupted my request; I accepted edits with diagnostics visible (Themes 1 and 2). [Error fix examples](Walkthrough%20Details.md#4.%20Fixing%20errors)

**Step 5. Previewing.** **Stuck:** I didn't resolve whether one-second refresh applied in preview (Theme 2). [Refresh question](Walkthrough%20Details.md#5.%20Previewing%20and%20live%20data)

**Step 6. Claude over MCP.** **Good:** Render/check loop (Theme 2). **Stuck:** Code needed manual handoff to Studio (Theme 1). [MCP build](Walkthrough%20Details.md#6.%20Building%20the%20same%20page%20with%20Claude%20over%20MCP)

**Step 7. Inviting a teammate.** **Good:** My second account signed up through the invitation; edits appeared live. [Invitation test](Walkthrough%20Details.md#7.%20Inviting%20a%20teammate)

**Step 8. GitHub and publishing.** **Good:** GitHub commits appeared in Studio, and Studio publishes appeared on GitHub. **Stuck:** With unpublished Studio edits present, a later GitHub addition appeared as a pending deletion in Studio (Theme 1). [GitHub walkthrough](Walkthrough%20Details.md#8.%20Connecting%20GitHub%20and%20publishing)

**Step 9. Returning.** **Stuck:** A listed chat returned “chat not found” (Theme 1). [Chat history](Walkthrough%20Details.md#9.%20Coming%20back%20later)

**Navigation:** The Support button on the Schedules page did nothing when clicked. [Navigation notes](Walkthrough%20Details.md#General%20navigation)

**Smaller wishes:** Which connections can this project and its agent use, and can I narrow them per project and investigation? I'd also use a copy button under agent responses and voice input. [Data scope](Analysis%20and%20Customer%20Reasoning.md#Data%20scope) · [Copy and voice](Analysis%20and%20Customer%20Reasoning.md#Smaller%20wishes)

**AI use:** I used Studio's agent and Claude for building, and AI to organize dictated notes, research sources, and help draft the feedback. I chose the observations and emphasis.

**Optional supporting notes:** [Full walkthrough](Walkthrough%20Details.md) · [Customer reasoning](Analysis%20and%20Customer%20Reasoning.md) · [How I used AI](How%20I%20Used%20AI.md) · [Sources and references](References.md)
