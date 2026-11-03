**Time spent:** about 1.5 to 2 hours building and exploring the product, and 3 to 4 hours on market research, analysis, and further exploring the product.

**What I built:** A live homelab health dashboard using Neon as the db. I built with Studio's agent, tried a separate version with Claude through MCP, tested collaboration with a second account, and connected GitHub.

Writing the dashboard as code with the agent was the best part of Studio for me. I could see the Markdown and SQL as it worked, its suggestions came from my actual data, and the live preview helped me follow the build. I also like having a framework focused on BI. The agent could help build and repair the report, but keeping the conversation and task context was less consistent: a repair interrupted my existing request, and later I couldn't reopen a previous chat. I'd like that context to carry through my work, with the agent available during setup too. For a data team maintaining reports for others, that could mean less re-explaining and more time checking the result.

### What I Did

**1. Creating the project.** I created Home Lab Analytics and asked the agent to build a live dashboard from my Neon data, starting with a broad request rather than a detailed specification. [Starting prompt](Walkthrough%20Details.md#1.%20Creating%20the%20project)

**2. Connecting my database**
- **Stuck:** Connecting Neon took me outside the project, away from the agent. Going back for help meant re-entering some details; I wondered whether the agent could do setup with me.
- **Stuck:** I also struggled to choose between direct and synced connections and find the pages the docs described. [Connection walkthrough](Walkthrough%20Details.md#2.%20Connecting%20my%20database)

**3. Building the report with the agent.** **Good:** It suggested components based on my data and pointed out telemetry I wasn't collecting yet. I added sources based on those suggestions. I could see the queries and watch components appear in preview as it wrote them. [Suggestions and build sequence](Walkthrough%20Details.md#3.%20Building%20the%20report%20with%20the%20agent)

**4. Fixing errors**
- **Good:** Sending a diagnostic to chat included a useful ready-made prompt.
- **Stuck:** Using it interrupted my temperature request; I had to ask again. I also accepted changes with about five errors showing, without knowing what had been checked. [Repair examples](Walkthrough%20Details.md#4.%20Fixing%20errors)

**5. Previewing and live data.** **Stuck:** I couldn't tell whether my one-second refresh setting applied in preview or only after publishing. I didn't resolve this during the walkthrough. [Refresh question](Walkthrough%20Details.md#5.%20Previewing%20and%20live%20data)

**6. Building the same page with Claude over MCP**
- **Good:** I liked that Claude rendered and checked its page before handing it over.
- **Stuck:** It couldn't save the page through MCP, so the handoff was code for me to paste into Studio. [MCP build and handoff](Walkthrough%20Details.md#6.%20Building%20the%20same%20page%20with%20Claude%20over%20MCP)

**7. Inviting a teammate.** **Good:** Using a second account, I could sign up through the invitation link without an existing Evidence account. Changes showed up live in both sessions. [Invitation test](Walkthrough%20Details.md#7.%20Inviting%20a%20teammate)

**8. Connecting GitHub and publishing.** **Stuck:** Studio kept sending me back to GitHub even though its app was already installed with access to all repositories. Switching to selected repositories and choosing my new repo made it appear in Studio. [GitHub setup workaround](Walkthrough%20Details.md#8.%20Connecting%20GitHub%20and%20publishing)

**9. Coming back later.** **Stuck:** Reopening a recent chat on my main account gave “chat not found,” even though its title was still listed. I couldn't get back to the conversation. [Chat history issue](Walkthrough%20Details.md#9.%20Coming%20back%20later)

**General navigation**
- **Stuck:** The Support button on Schedules did nothing when I clicked it. [Navigation notes](Walkthrough%20Details.md#General%20navigation)

### My Feedback

One customer task I kept in mind was a data team maintaining guided account-health analysis for customer-success colleagues. I pictured the team updating the method and checking the results, while the colleague needs an account assessment they can understand and use. Evidence's account-health skill example helped make that workflow concrete ([McAskill, “That Dashboard”](https://evidence.dev/blog/that-dashboard-should-be-a-skill)).

**A shared framework for BI.** A big part of the appeal for me is having a framework and runtime focused on BI: queries, reusable metrics, components, and the reports they produce ([McAskill, “Evidence Core”](https://evidence.dev/blog/evidence-core)). I see potential for this to become a the standard way for data teams to express and maintain analysis in the future. In the account-health example, that could mean reusing definitions and patterns in the next report or skill.  [Framework and reuse](Analysis%20and%20Customer%20Reasoning.md#A%20framework%20focused%20on%20BI)

**Keeping the conversation across Studio.** I'd like one continuing conversation: a main chat view for exploring what to build, and a code view with the same conversation alongside the files. That could keep what I liked about seeing the queries while reducing backtracking. I'd also like that help to carry through connection setup and other Studio workflows, so a maintainer isn't repeatedly explaining the task before checking the report their colleagues will use.

It might also make the framework easier to learn and help less technical teammates understand the repo. I haven't tested that possibility. [Chat and code views](Analysis%20and%20Customer%20Reasoning.md#Agent%20integration)

**Knowing what the agent did and checked.** The diff showed the edit, but I couldn't tell what had been checked. I'd like the agent to say what changed, what it validated, and what remains open, with a record I can return to after an interruption. That would help a maintainer review a report and later explain a result to a reader. [Checks and action history](Analysis%20and%20Customer%20Reasoning.md#What%20the%20agent%20did%20and%20checked)

**Which data a project and its agent can reach.** I wasn't clear which connections a project and its agent could use. I'd like project-scoped connections and a visible way to choose the data for one investigation. For a data team serving several groups, I think that would make the intended scope easier to understand before sharing a report. I haven't established whether that configuration already exists; choosing relevant data and enforcing access are separate questions. [Connection and investigation scope](Analysis%20and%20Customer%20Reasoning.md#Data%20scope)

**Smaller wishes.** I'd use a copy button under agent responses to move SQL or explanations into a ticket or doc, and voice input to describe a report aloud. [Copy and voice input](Analysis%20and%20Customer%20Reasoning.md#Smaller%20wishes)

**AI use:** I used Studio's agent and Claude for building, and AI to organize dictated notes, research sources, and help draft the feedback. I chose the observations and emphasis.

**Optional supporting notes:** [Full walkthrough](Walkthrough%20Details.md) · [Customer reasoning](Analysis%20and%20Customer%20Reasoning.md) · [How I used AI](How%20I%20Used%20AI.md) · [Sources and references](References.md)
