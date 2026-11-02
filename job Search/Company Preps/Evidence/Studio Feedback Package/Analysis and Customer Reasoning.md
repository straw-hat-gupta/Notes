# Analysis and customer reasoning

%% Skeleton. The deeper reasoning behind Part 2 of the main note. Each theme: what I saw (link back to the walkthrough), my labeled guess at why it works this way, why it matters to Evidence's customers, and what I'd change or found myself wanting. Every customer claim and every "exists / not documented" claim about Evidence uses an MLA in-text citation from References. %%

Back to [Evidence Studio Feedback](Evidence%20Studio%20Feedback.md) · Sources: [External Research and Sources](External%20Research%20and%20Sources.md) · [References](References.md)

## Who I kept in mind

I kept two people in mind: the person maintaining reports, queries, and shared definitions, and the colleague using those reports to answer a business question. Evidence describes readers asking questions and saving shareable insights, with reports and project knowledge supplying context (["Analytics Agent"](https://evidence.dev/product/analytics-agent)). My reasoning is that reducing the maintainer's repeated work leaves more time to check what readers will see. This is a customer lens for interpreting my experience, not a customer study.

The concrete task I chose is a data team maintaining guided account-health analysis for customer-success colleagues. Evidence describes an unnamed customer turning a complex health dashboard into a skill that asks relevant questions and guides the analysis. The original dashboard included product usage, support history, and renewal information; its growing set of inputs required knowledge of the customer's methodology ([McAskill, “That Dashboard”](https://evidence.dev/blog/that-dashboard-should-be-a-skill)).

In the scenario I pictured, the data team owns the method and its maintenance, while the customer-success colleague needs a relevant, explainable assessment. Those roles are my interpretation of the workflow, not disclosed details about the unnamed customer. It gives the feedback a practical question: can the maintainer update and check the method, then explain a changed assessment to the colleague using it? I did not build or test this account-health scenario.

## Agent integration

**What prompted this:** the agent helped me build the report, but I left it behind during connection setup and had to repeat a request after a repair interrupted it. My guess is that the interface separates report work from setup in a way that made those transitions harder; I haven't inspected the implementation.

**What I'd keep:** the visible code and the ability to shape the agent through version-controlled context and skills. I noticed `agent/` in the project but did not edit it. The docs describe always-loaded context, on-demand skills, and CLI development with an agent of your choice (["Evidence Agent," Evidence Docs](https://docs.evidence.dev/features/evidence-agent); ["CLI"](https://docs.evidence.dev/cli)).

**What I'd explore:** a main chat view showing generated outputs, and a file/preview view with the same conversation alongside it. I'd like the agent to help with connection and team setup within my permissions too. The editor already supports some project/page settings; this wish concerns carrying help across the surrounding workflow (["Editing"](https://docs.evidence.dev/editing)).

For a maintainer, that could reduce re-explaining and backtracking without hiding the code they need to review. Seeing the files alongside the same conversation might also help someone learn the framework and understand how a maintained project is organized. That could give technical and less technical colleagues a shared reference when discussing changes. These are possibilities to test, not outcomes I measured.

## What the agent did and checked

**What prompted this:** I accepted changes while errors were visible, a repair interrupted requested work, and I later couldn't reopen a chat. Claude's render/check loop was a useful contrast in how the result was handed over. The agent already shows a diff; what I wanted was clarity about checks and unfinished work.

**What already exists:** Evidence describes queries and sources behind answers, with the prompt and implementation notes saved alongside insights (["Analytics Agent"](https://evidence.dev/product/analytics-agent)). That is useful provenance; I did not test a complete record of agent actions during this walkthrough.

**What I'd like:** a concise completion note saying what changed, which checks ran, and what remains open, plus a record of queries, edits, and check results I can return to. This would help the maintainer review an agent-made change and answer a reader asking where a number came from. A repair should also retain the original request so the record and the actual work stay aligned. I don't know whether the readiness mismatch came from unavailable diagnostics, missed feedback, or something else.

In the account-health scenario, I would want the maintainer to distinguish a changed method from changed customer data when a colleague asks why an assessment moved. That is the practical value I see in keeping the change, its checks, and the sources understandable together.

## Data scope

**My question:** which connections can this project and its agent use, and how do I make that scope explicit? The CLI docs describe using the organization's data connection; that does not establish every project's effective access (["Connect Your CLI to Your Data"](https://docs.evidence.dev/cli/connections)).

I'd prefer project-scoped connections and a visible choice of data for an investigation. For a data team serving several groups, I think that could make the intended scope easier to understand before sharing a report. Central connections may also save repeated administration; I haven't tested that tradeoff.

Choosing relevant data is different from enforcing who can access it. Evidence documents table/row controls and directs users of direct connectors to connector-specific rules (["Row Level Security"](https://docs.evidence.dev/features/row-level-security)). I did not test those controls or establish whether hosted project-specific connection configuration exists. This is a question and a preference, not a claim that the agent can query everything.

## Smaller wishes

| What I found myself wanting | Why I would use it |
| --- | --- |
| A copy button under agent responses | Move SQL or an explanation into a ticket or doc when discussing or investigating a report. This is a convenience wish, not a verified claim that no copy interaction exists. |
| Voice input in the agent | Describe the report or investigation aloud. I used dictation for these notes and would like that option in Studio; I haven't measured whether it would be faster for other users. |

The Docs and Support observations stay in the walkthrough rather than being repeated as additional wishes here.
