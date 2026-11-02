# Evidence product feedback: planning

Saved 2026-11-02 (updated with Sam's edits, rev 328) from the Claude Doc [Evidence product feedback: planning](https://claude.ai/artifact/BifMambPCuPMv7jv4HnANQ). The Claude Doc is the live version; this is a copy. Sources: [[Home Lab Analytics - Review Log]], [[Product Feedback Notes]], [[Product Review Findings]], [[Evidence Studio - Product Review]], [[Target Market and Customer Needs]], and the [customer research doc](https://claude.ai/artifact/BvGsmju9j1JyMsrqXMmg7W).

## How the notes should read

The notes are my observations from using Studio, written from the user's seat. They are not a list of things Evidence should build. Evidence says being close to the user matters most to them, so the notes should show I was thinking about their users the whole time.

Taken as a whole, the notes should answer these four questions without listing them as headings:

1. Where did I get stuck?
2. What surprised me?
3. What would I change?
4. Why do I think things work the way they do?

**Voice rules:**

- Write "I tried X, I expected Y, I saw Z", not "you should add X".
- A wish stays a wish ("I found myself wanting a copy button"). Every time I suggest a change, I add one line on why it would help Evidence's customers, not just me.
- Don't mention competitors anywhere. Research findings show up only as reasoning about Evidence's own customers.
- Say plainly when something happened once, in one session, or wasn't reproduced.

**Structure:** a short overall verdict at the top, then Part 1 (what I did, by stage, brief), then Part 2 (analysis).

## Top of the notes: overall feedback

The opening is a short verdict: mostly positive about building in code with the agent, then one or two sentences on what I was missing. Here is a starting draft in my voice for me to rewrite:

> I built a live homelab health dashboard in Studio on top of my Neon database, then tried the same build with Claude over MCP and tested a second account and GitHub publishing. Building was the best part. The agent was very good at the Evidence framework, its suggestions came from my actual data, and I liked staying close to the code: the markdown file was right there, and I could see exactly what queries were running at each step. Where I struggled was everything around the build. The agent felt like a helper on the side of the editor more than part of Studio's workflows, so setup, repairing errors, picking up old chats, and publishing were where I lost context or had to work out what state things were in myself.

**Points the opening must carry:**

- **Positive:** writing reports as code with the agent, closeness to the code and queries, suggestions grounded in my data, live preview. *(Sam, HLA-10 to 12, HLA-17, and Sam's 2 Nov message)*
- **Wanting:** the agent isn't connected to the rest of Studio, and I wanted a view where the agent is central, not only a side panel. *(Sam, HLA-44, HLA-47)*

## Part 1: what I did, by stage

Keep each stage to a few short lines in the final notes. The tags are **Good**, **Stuck**, **Surprised**, and **Wished**. Everything here is from my own log unless it is marked agent-logged. Source references are for me and come out of the final version.

### 1. Creating the project

- **Good:** I created Home Lab Analytics and typed a broad, plain request into the agent sidebar ("help me create a live dashboard from my Neon data"). It took that as a starting point without needing a spec. *(log, 31 Oct)*

### 2. Connecting my database

- **Stuck:** The agent sent me to the Connectors page, which was outside my project, so the agent wasn't there with me. I was partway through the add-connection form on the warehouse page. When I went back to ask the agent something and then returned, what I had entered was gone. *(HLA-01)*
- **Stuck:** The agent gave me a link to the connections page, but clicking it didn't go anywhere. *(HLA-02)*
- **Stuck:** I couldn't work out how to set a sync schedule. The docs pointed to a Sources page and a Connectors item in the sidebar that I couldn't find. *(HLA-04, HLA-06)*
- **Surprised:** The agent changed its recommendation from a synced connector to a direct one, and I still couldn't tell which was better for me. I connected using the Neon owner user without creating a read-only role. *(HLA-05)*
- **Surprised:** When I asked about the synced connector, the agent started building the dashboard instead. *(HLA-08)*
- **Wished:** that the agent could do the connection setup with me, asking for the details it needed. *(HLA-01)*
- **Wished:** a copy button under agent responses. *(HLA-07)*

### 3. Building the report with the agent

- **Good:** It looked at my data and suggested what to add, including telemetry I wasn't collecting yet. I liked them enough to add the sources it recommended. *(HLA-10 to 11)*
- **Good:** Changes were staged for me to accept, and the components appeared in preview as the agent wrote them. *(HLA-10, HLA-12)*
- **Good:** The agent was very good at the Evidence framework. Being in the markdown file meant I was close to the code and could see exactly which queries were being sent at each stage. *(HLA-17, Sam's 2 Nov message)*
- **Good:** I can keep asking questions about a report as the connected data changes. *(HLA-35)*
- **Wished:** voice-to-text input in the agent. *(HLA-22)*

### 4. Fixing errors

- **Good:** Hovering over an error lets me send it to chat with a ready-made, concise prompt, and that saved me time. *(HLA-15)*
- **Stuck:** The agent asked me to accept changes while I could see about five errors at the top of the page, something about a string type in a max function. I accepted anyway. *(HLA-13)*
- **Stuck:** Sending an error to chat interrupted the temperature components I had already asked for, and it didn't finish. I had to prompt the agent again before it built them. *(HLA-16)*
- **Surprised:** Warnings went to chat with the same "component error" prompt as errors. *(HLA-18)*
- **Wished:** maybe a separate agent for errors, so a fix doesn't interrupt the conversation I'm in. I'm not sure it's a big deal. *(HLA-16)*

### 5. Previewing and "live" data

- **Stuck:** I couldn't tell whether preview refreshes every second or only the published page does. *(HLA-14)*
- **Agent-logged, not checked by me:** the Postgres docs described only a synced source while the direct connection was live, and the documented refresh limits disagreed. *(HLA-26 to 27)*

### 6. Building the same page with Claude over MCP

- **Good:** Setup was smooth. Claude used Evidence's render tool to check and fix its page before handing it over, and the page had no errors. *(HLA-34, HLA-36)*
- **Stuck:** Claude couldn't save the page, so it gave me code to paste into Studio. *(HLA-36; tool details agent-logged in HLA-24)*
- **Agent-logged, not checked by me:** table listing returned nothing while SQL saw the tables, and render output was too large for the client. *(HLA-25, HLA-29)*

### 7. Inviting a teammate

- **Good:** I found the invite option easily. The person didn't need an existing Evidence account, and edits showed up live in both sessions. *(HLA-03, HLA-37)*
- **Stuck:** I needed the docs to understand the roles, especially viewer versus org viewer. *(HLA-03)*
- **Question I had:** could someone less technical maintain this without learning the whole Git workflow? *(HLA-23)*

### 8. Connecting GitHub and publishing

- **Stuck:** Studio didn't recognize my existing GitHub installation until I switched from all repositories to selected repositories. *(HLA-39)*
- **Surprised:** A new warning on Publish said remote changes would be overwritten, without showing which ones. It made me wonder what happens when one person edits in a code editor and another in Studio. Force Publish wasn't checked by default, and I went ahead with it. *(HLA-40, screenshot)*

### 9. Coming back later, and after publishing

- **Stuck:** After I closed and reopened my main account, a recent chat still showed its title but said "chat not found". I lost that conversation. *(HLA-38)*
- **Question I had:** does every project get every connection, or do I choose which connections a project gets? *(HLA-41, HLA-43)*
- **Wished:** connections scoped per project. *(HLA-45)*
- **Wished:** a way to point the agent at only the data I want to analyze, instead of telling it in the prompt to ignore the rest. *(HLA-46)*

### General navigation (29 Oct notes)

- **Surprised:** The Docs button opened a separate site, while the other buttons next to it stayed in Studio, so I expected in-app docs. Studio does show tooltips that link functions to the docs.
- **Stuck:** The support button on the Schedules page did nothing when I clicked it.

## Part 2: analysis

This part says why the Part 1 moments matter and who they matter to. Each theme has four pieces: what I saw, my guess at why it works that way, why it matters to Evidence's customers, and what I'd change. Guesses about causes are labeled, because I haven't seen the code behind Studio.

### Who I kept in mind

From Evidence's product pages, pricing, and public examples, my read is that the core customer is **a data team that owns a reusable reporting system for people who don't maintain the code**. Maintainers are senior analysts, analytics engineers, and sometimes app engineers. Readers are operators, leaders, and sometimes external customers. The Team plan is a flat fee with unlimited users, which suggests most people in a customer org are readers, not authors. Public examples include a company posting for an analyst to own recurring reporting in Evidence, and a research group pairing dataset releases with quality dashboards. *(Inferred from the Target Market note and customer research; not a disclosed customer profile.)*

The Part 2 themes come back to three things those customers need: reports they **revise** over time, numbers readers can **trust**, and agent-made changes someone can **review**.

### Theme 1: the agent is great in the file and loosely connected to Studio

- **What I saw:** Inside the markdown file, the agent was strong. Outside it, I lost it: during connector setup, when a repair interrupted my request, when an old chat disappeared, and around GitHub and publishing. *(Part 1, stages 2, 4, 8, 9)*
- **Why I think it works this way (guess):** The agent seems scoped to the project and its files, while connectors, teams, and Git live at the organization level outside the project. That would explain why the agent couldn't come with me to setup and only gave me a link.
- **Why it matters to customers:** For a team that owns reporting, the value of reports as code shows up on the second and tenth revision, not the first build. Every time context is lost, they pay again. Setup is also where a new maintainer decides whether to keep going.
- **What I found myself wanting:** one continuing conversation with two views. A chat view where the agent is the main surface and I can see and organize what it makes, and an IDE view with the files and preview and the same conversation alongside. The agent could also help with connections and team setup within my permissions. I'd keep the closeness to the code, because seeing the exact queries is what made me trust the output. *(HLA-44, HLA-47)*
- **Justification to include:** developers increasingly start with an agent, so making it central fits how Evidence's maintainers already work. Keeping the IDE view preserves the code review workflow those teams chose Evidence for. Whether this would bring in less technical authors is a hypothesis, and I'd say so.

**Added 2 Nov (HLA-48), checked against Evidence's docs:**

- **What I like:** the `agent/` directory. Context files are always loaded, skills load on demand, and both are version-controlled per project and ship through Git. Teams that are good with AI can shape the agent that maintains their reports. I noticed it in the project structure but didn't edit it during the walkthrough. *(Exists: [Evidence Agent docs](https://docs.evidence.dev/features/evidence-agent))*
- **Why that matters:** people used to working with agents can treat an Evidence project like any other repo. They bring their own agent through the CLI, keep instructions in files, and review changes in PRs with preview links. *(Exists: [CLI docs](https://docs.evidence.dev/cli))* An agent-centric Studio view would sit on top of that, not replace it.
- **What I'd add to the case for an agent-centric view:** it may lower the first hill of learning a new framework, even a simple one. It could also show less technical users what a maintained repo looks like, so they and technical teammates share expectations and collaborate more easily. *(Both are hypotheses. The second connects to my question in stage 7 about less technical maintainers.)*
- **What isn't there yet, as far as the docs show:** the agent acting on Studio's own workflows and settings, such as connections and team members. The agent docs cover answers, insights, and page edits.

### Theme 2: "done" didn't tell me what had been checked

- **What I saw:** I was asked to accept with errors visible, warnings were sent as errors, and an interrupted request never finished. With Claude over MCP, Evidence's render tool let it check its own page before handing it over. *(Stages 4 and 6)*
- **Why I think it works this way (guess):** The native agent seems to report completion based on its edit, without reading the editor's diagnostics or the render first. The MCP path shows the checking tools already exist.
- **Why it matters to customers:** Readers act on these numbers in KPI reviews, account health checks, and release reports. As agents make more of the changes, the person approving them needs to know what was checked. This connects to the review bottleneck Sean described, and I'd mention that in one sentence at most.
- **What I'd change:** before asking me to accept, show what changed, what was checked, and what's still open. Keep warnings and errors distinct. The agent already shows a diff whenever it makes changes; what I was missing was what had been checked.

### Theme 3: mixing Studio and Git editing

- **What I saw:** GitHub recognition needed a workaround, I needed the docs to understand roles, and the overwrite warning didn't show what would be replaced. *(Stages 7 and 8)*
- **Why I think it works this way (guess):** Studio and the Git repo are two places the same report can change, and Publish has to reconcile them.
- **Why it matters to customers:** Evidence's pitch is that analysts and engineers can maintain the same reports. That's exactly the team that would see this dialog, and the less technical person is the one least able to judge it.
- **What I'd change:** show which changes are at risk at the point of decision. I didn't lose any work, and I'd say that.

### Theme 4: which data a project and its agent can reach

- **What I saw:** After building, I wasn't sure which data a project, and the agent in it, could reach. *(Stage 9)* Readers use the agent in the report itself, through the chat tab in the side menu.
- **Why it matters to customers:** A data team serving several groups needs to know which data each project and its agent can reach before sharing it.
- **What I found myself wanting:** connections scoped per project, and a visible way to choose which data an investigation uses. Justification: a data team serving several groups wants each report to reach only the data it's meant to. I'd frame this as a question, because central connections also save admin work.

### Theme 5: seeing what the agent did

- **What I saw:** I had to piece together the agent's work myself. It asked for acceptance with errors showing, a repair interrupted a request, and a whole conversation disappeared. *(Stages 4 and 9)*
- **What already exists (checked):** answers show the query and source behind each number, and saved insights keep their prompt and implementation notes ([Analytics Agent page](https://evidence.dev/product/analytics-agent)). Enterprise streams audit logs to tools like Datadog and Sentry, but the page doesn't say whether agent activity is included ([Enterprise page](https://evidence.dev/product/enterprise)). Context changes can be checked in a deploy preview before merging ([launch post](https://evidence.dev/blog/evidence-agent)).
- **What I couldn't find:** a trace or log of every step the agent took, or evals. My earlier note that evals already exist came from other research, not Evidence, so the final notes won't say Evidence has them.
- **What I found myself wanting:** a way to trace and log what the Evidence Agent does, possibly by plugging in an external service. Durable execution for robustness was a tentative thought; observability is the part I'm sure about.
- **Why it matters to customers:** a data team approving agent changes, or answering a reader who asks "where did this number come from", needs a record of what the agent queried and changed. It also helps them tune their context and skills over time.

### The smaller wishes

| Wish | Why it would help Evidence's users |
| --- | --- |
| Copy button under agent responses (HLA-07) | Maintainers paste SQL, explanations, and answers into tickets, PRs, and docs |
| Voice-to-text in the agent (HLA-22) | Describing a report out loud may be faster than typing it (my own reason, not backed by research) |
| Links in agent answers that navigate (HLA-02) | Setup steps are only useful if I can get to the page |
| In-app docs instead of a separate site (29 Oct notes; tooltips already link to docs) | Keeps a new maintainer in Studio while learning components |
| Support button on Schedules that responds (29 Oct notes) | Schedules are one way reports reach readers, so help there matters (inferred) |

## Sources and evidence labels

Nothing new was tested in the product for this plan.

| Source | Used for |
| --- | --- |
| [[Home Lab Analytics - Review Log]] (31 Oct to 2 Nov, HLA-01 to HLA-48) | Part 1, from my own quoted words in each entry |
| [[Product Feedback Notes]] (29 Oct) | Docs button, Schedules support button, tooltip question |
| My 2 Nov messages to Claude | Closeness to the code, agent-centric view, structure, HLA-48 ideas |
| [[Product Review Findings]], [[Evidence Studio - Product Review]] | Cross-check of themes |
| [[Target Market and Customer Needs]], [customer research doc](https://claude.ai/artifact/BvGsmju9j1JyMsrqXMmg7W) | Who I kept in mind; Evidence-side findings only |

**Agent-logged** means Claude recorded it during the MCP run and I didn't reproduce it. These items either stay out of the final notes or carry that caveat.

## Gaps for Sam to fill

These are missing from the logs. Claude hasn't guessed at any of them.

- [x] **Other sessions:** did I use Studio after 31 Oct? If so, what happened that should go in Part 1? No.
- [x] **Stage 2:** which fields were wiped, and was there a save button I hadn't pressed? I was partly done filling in the add-connection form on the warehouse page.
- [x] **Stage 4:** did I accept with the errors showing? Did the temperature components ever get built? I accepted with the errors showing. They did get built, but I had to prompt it again.
- [x] **Stage 5:** did I ever find out whether preview refreshes live? No.
- [x] **Stage 8:** was Force Publish checked by default, and did I go through with it? It was not checked, and I went through with it.
- [x] **Stage 9:** did the lost chat ever come back? No.
- [x] **Agent-logged items:** reproduce the green "0 °C" missing value myself, or drop it. Drop it.
- [x] **My judgment:** my log says the agent felt like a smaller model tuned well for Evidence (HLA-17). That's a guess about their internals, so leave it out unless I want to raise it as a question. Leave it out.
- [ ] **My judgment:** mention Sean's review-bottleneck point in Theme 2, or keep it for the interview? My note: the agent does show the diff whenever it makes changes. (Still to decide on the Sean point.)
- [x] **Reader view:** one short pass as a reader of the published report would make Theme 4 firsthand. Keep this out; the notes focus on my perspective as a user making reports.
- [x] **Theme 1 (2 Nov):** did I edit `agent/context/instructions.md` or add a skill during the walkthrough? If yes, it moves into Part 1 as a firsthand Good. If not, frame it as something I noticed in the project structure. I did not.
