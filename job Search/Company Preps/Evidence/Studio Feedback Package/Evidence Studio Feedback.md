# Evidence Studio: notes from building with it

%% Skeleton. This is the one note the Evidence team reads first. Keep every section brief and link out for evidence and deeper reasoning. Voice: what I did, what I saw, what I wished for, and why I think it matters to Evidence's users. No competitor mentions. %%

**Time spent:** about 1 to 2 hours building and exploring the product, and 3 to 4 hours on market research and analysis.

**What I built:** _To write: one or two sentences. A live homelab health dashboard on my Neon database with the Studio agent, the same page built with Claude over MCP, a second account to test teamwork, and GitHub publishing. Dates: 29 to 31 October 2026._

**Other notes in this folder:**

- [Walkthrough Details](Walkthrough%20Details.md): the fuller account of each stage
- [Analysis and Customer Reasoning](Analysis%20and%20Customer%20Reasoning.md): why I think each point matters to Evidence's customers
- [External Research and Sources](External%20Research%20and%20Sources.md): every outside claim and the source it rests on
- [How I Used AI](How%20I%20Used%20AI.md): how AI helped with building, note-taking, research, and writing
- [References](References.md): every citation in one place, in MLA format

## Summary

%% Working draft, 2 Nov. Direction chosen by Sam: approachable report writing with visible code/queries; continuity reduces repeated work and leaves more time to check what readers see. Save the shared chat/IDE proposal for the analysis. Audience: data team and its business readers. Main-note target: about 1,000 words, retaining every walkthrough stage. Wording remains editable. %%

Writing the report as code with the agent was the best part of Studio for me. I could see the Markdown and SQL as it worked, its suggestions came from my actual data, and the live preview helped me follow what it was building. I wanted that experience to carry further into Studio: connecting data, fixing errors, and publishing without losing the conversation or the task. For a data team maintaining reports that other people rely on, I think that continuity could mean less time repeating work and more time checking and improving what readers will see.

## Part 1: what I did

%% One short block per stage: what I did, then my comments tagged Good, Stuck, Surprised, or Wished. Each stage ends with a link to its section in Walkthrough Details. %%

### 1. Creating the project

_To write._ · [Details](Walkthrough%20Details.md#1.%20Creating%20the%20project)

### 2. Connecting my database

- **Stuck:** Connecting Neon took me outside the project, away from the agent. Going back for help meant re-entering some details; I wondered whether the agent could handle setup with me.
- **Stuck:** I also struggled to choose between direct and synced connections and find the pages the docs described.

[Details](Walkthrough%20Details.md#2.%20Connecting%20my%20database)

### 3. Building the report with the agent

_To write._ · [Details](Walkthrough%20Details.md#3.%20Building%20the%20report%20with%20the%20agent)

### 4. Fixing errors

- **Good:** Sending a diagnostic to chat included a useful ready-made prompt.
- **Stuck:** Using it interrupted my temperature request; I had to ask again. I also accepted changes with about five errors showing, without knowing what had been checked.

[Details](Walkthrough%20Details.md#4.%20Fixing%20errors)

### 5. Previewing and live data

_To write._ · [Details](Walkthrough%20Details.md#5.%20Previewing%20and%20live%20data)

### 6. Building the same page with Claude over MCP

_To write._ · [Details](Walkthrough%20Details.md#6.%20Building%20the%20same%20page%20with%20Claude%20over%20MCP)

### 7. Inviting a teammate

_To write._ · [Details](Walkthrough%20Details.md#7.%20Inviting%20a%20teammate)

### 8. Connecting GitHub and publishing

**Stuck:** Studio kept sending me back to GitHub even though its app was already installed with access to all repositories. Switching to selected repositories and choosing my new repo made it appear in Studio.

[Details](Walkthrough%20Details.md#8.%20Connecting%20GitHub%20and%20publishing)

### 9. Coming back later

_To write._ · [Details](Walkthrough%20Details.md#9.%20Coming%20back%20later)

### General navigation

_To write._ · [Details](Walkthrough%20Details.md#General%20navigation)

## Part 2: what I think it means

%% One short paragraph per theme: the point, the customer reason in one line, and a link to the full reasoning. %%

### The agent is great in the file and loosely connected to Studio

_To write._ · [Reasoning](Analysis%20and%20Customer%20Reasoning.md#Agent%20integration)

### "Done" didn't tell me what had been checked

_To write._ · [Reasoning](Analysis%20and%20Customer%20Reasoning.md#What%20was%20checked)

### Mixing Studio and Git editing

_To write._ · [Reasoning](Analysis%20and%20Customer%20Reasoning.md#Studio%20and%20Git%20editing)

### Which data a project and its agent can reach

_To write._ · [Reasoning](Analysis%20and%20Customer%20Reasoning.md#Data%20scope)

### Seeing what the agent did

_To write._ · [Reasoning](Analysis%20and%20Customer%20Reasoning.md#Agent%20observability)

### Smaller wishes

_To write: a short list._ · [Reasoning](Analysis%20and%20Customer%20Reasoning.md#Smaller%20wishes)

## Limits of these notes

_To write: one evaluator, one personal use case, observations not reproduced unless stated, no access to Studio's internals._
