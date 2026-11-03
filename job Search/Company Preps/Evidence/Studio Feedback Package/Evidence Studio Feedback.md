**Time spent:** about 1.5 to 2 hours building and exploring, and 3 to 4 hours on research, analysis, and further exploration.

**What I built:** A live homelab health dashboard on Neon, using Studio's agent, with a separate Claude/MCP build, a second-account collaboration test, and GitHub setup.

I ended with a promising first dashboard I'd keep using and develop further. Building was the best part: suggestions came from my data, and I could follow the Markdown, SQL, and preview. The friction came when I needed help beyond the report file or had to recover task context. My main wish is for the agent to work more directly with Studio's workflows, carrying the conversation and task through setup, repairs, and return visits. Clearer checking would support that: tell me what changed, what was checked, and what remains open. For maintainers, that could mean less re-explaining and more time checking the result.

### Who I Had in Mind

I pictured a data team keeping an account-health assessment correct as data and methods change, then explaining a changed result to customer-success colleagues. Evidence's account-health skill story informed that scenario; the roles are my interpretation ([McAskill, “That Dashboard”](https://evidence.dev/blog/that-dashboard-should-be-a-skill)).

My homelab is a monitoring use case, outside that business-reporting scenario. What carries over is the author's loop of building, checking, returning, and revising, plus questions about data freshness. It gives me a way to examine that workflow, rather than evidence of what those customers need most.

### My Feedback

**1. An agent that works with Studio and keeps the task.** During setup I left the agent behind; a repair displaced my request; later I couldn't reopen a chat (stages 2, 4, and 9). I'd like the agent to help carry out Studio workflows, including connection and team setup within my permissions, while retaining the task and conversation. The editor already supports some settings changes (["Editing"](https://docs.evidence.dev/editing)).

I'd start with guided connection setup alongside the same agent, repairs that retain the original request, and reliable reopening of listed chats. Those would reduce backtracking for a maintainer preparing reports for others. A larger direction I'd explore is a main chat view and a file/preview view sharing one conversation. I'd judge the improvement by whether I can complete setup or resume work without navigating back to explain myself again. [Agent integration](Analysis%20and%20Customer%20Reasoning.md#Agent%20integration)

**2. Knowing what changed and what was checked.** I accepted changes with about five errors showing; a separate repair response said the rendered section hadn't been inspected (stage 4). I appreciated Claude's render/check loop before handoff (stage 6). The diff showed the edit, but I wanted to understand its checks too.

I'd add a brief completion note before Accept: what changed, what was checked, and what remains open, saved so I can revisit it. That supports the continuing workflow above: a maintainer returning to a report can see where to pick up and what still needs review. In the account-health scenario, that could help explain the basis of a changed assessment. I'd judge it by whether I can tell which checks ran, including a render check, without reconstructing the conversation. Rendering alone doesn't establish that the numbers are correct. [Checks and history](Analysis%20and%20Customer%20Reasoning.md#What%20the%20agent%20did%20and%20checked)

**3. A shared framework for BI over time.** The longer-term appeal is a framework and runtime focused on BI, with queries, reusable metrics, components, and validation ([McAskill, “Evidence Core”](https://evidence.dev/blog/evidence-core)). As agents write more of the code, the value I see is in shared definitions, components, and checks that keep later reports consistent and understandable. Keeping the code and queries visible was already useful in my build.

I'd make reuse tangible with one definition carried into a second report and then revised. In the account-health scenario, that could mean maintaining a method once rather than rebuilding it for each output. The test I'd want is whether the second report, or a later definition change, takes less effort and stays understandable to the next maintainer. That would give me stronger grounds for the framework's lasting value than the first build alone. [Framework and reuse](Analysis%20and%20Customer%20Reasoning.md#A%20framework%20focused%20on%20BI)

### What I Did

**1. Creating the project.** **Good:** A broad request started Home Lab Analytics. [Starting prompt](Walkthrough%20Details.md#1.%20Creating%20the%20project)

**2. Connecting my database.** **Stuck:** Setup took me away from the agent; direct versus synced guidance and navigation confused me (Theme 1). [Connection walkthrough](Walkthrough%20Details.md#2.%20Connecting%20my%20database)

**3. Building.** **Good:** Data-grounded suggestions prompted me to add telemetry; I watched queries and components appear. [Build sequence](Walkthrough%20Details.md#3.%20Building%20the%20report%20with%20the%20agent)

**4. Fixing errors.** **Good:** Prepared repair prompts. **Stuck:** A repair interrupted my request; I accepted edits with diagnostics visible (Themes 1–2). [Repair examples](Walkthrough%20Details.md#4.%20Fixing%20errors)

**5. Previewing.** **Stuck:** I didn't resolve whether one-second refresh applied in preview (Theme 2). [Refresh question](Walkthrough%20Details.md#5.%20Previewing%20and%20live%20data)

**6. Claude over MCP.** **Good:** Render/check loop. **Stuck:** Code needed manual handoff to Studio (Theme 2). [MCP build](Walkthrough%20Details.md#6.%20Building%20the%20same%20page%20with%20Claude%20over%20MCP)

**7. Inviting a teammate.** **Good:** My second account signed up through the invitation; edits appeared live. [Invitation test](Walkthrough%20Details.md#7.%20Inviting%20a%20teammate)

**8. GitHub and publishing.** **Stuck:** Studio repeatedly sent me back to GitHub; switching an existing installation to selected repositories made my repo appear. [Workaround](Walkthrough%20Details.md#8.%20Connecting%20GitHub%20and%20publishing)

**9. Returning.** **Stuck:** A listed chat returned “chat not found” (Theme 1). [Chat history](Walkthrough%20Details.md#9.%20Coming%20back%20later)

**Navigation:** Docs opened a separate site where I expected integrated help; Schedules' Support button did nothing when clicked. [Navigation notes](Walkthrough%20Details.md#General%20navigation)

**Smaller wishes:** Which connections can this project and its agent use, and can I narrow them per project and investigation? I'd also use a copy button under agent responses and voice input. [Data scope](Analysis%20and%20Customer%20Reasoning.md#Data%20scope) · [Copy and voice](Analysis%20and%20Customer%20Reasoning.md#Smaller%20wishes)

I didn't test the published reader experience, the account-health scenario, or access controls; the second account was mine.

**AI use:** I used Studio's agent and Claude for building, and AI to organize dictated notes, research sources, and help draft the feedback. I chose the observations and emphasis.

**Optional supporting notes:** [Full walkthrough](Walkthrough%20Details.md) · [Customer reasoning](Analysis%20and%20Customer%20Reasoning.md) · [How I used AI](How%20I%20Used%20AI.md) · [Sources and references](References.md)
