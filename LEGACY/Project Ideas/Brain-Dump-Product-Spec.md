# Heap: Builder Brain-Dump Organizer

## Status

**Stage:** product concept and MVP specification  
**Working name:** Heap  
**Core stack:** Obsidian, private GitHub repository, GBrain, a self-hosted vault-curator service, local GPU models, optional Claude or Codex reasoning

## 1. Product summary

Heap is an Obsidian-first personal organization system for technical builders. It turns low-friction brain dumps into an evolving, connected workspace for projects, learning, career activity, people, ideas, and tasks.

The product is for people who regularly encounter technical topics, have project ideas, pursue several learning threads, build things, apply for jobs, meet people, and struggle to keep the resulting context organized.

**Core promise:** capture a thought without deciding where it belongs. The system preserves the original capture, finds related context, and safely organizes it into the existing workspace.

Heap is not an Obsidian replacement. Obsidian remains the writing and browsing interface. The private GitHub-backed vault remains the canonical source of truth. GBrain is the memory, retrieval, graph, and background-enrichment backend.

## 2. Target user

A technical builder who:

- is actively learning technical topics such as AI engineering, agent systems, networking, infrastructure, security, or system design;
- has multiple active or possible projects;
- uses notes for research, ideas, plans, contacts, and work history;
- wants quick mobile capture, especially voice dictation;
- wants organization and continuity without constant manual filing;
- prefers Markdown, Git history, self-hosting, and provider flexibility.

## 3. Product principles

1. **Capture first, organize later.** The user should not choose folders, templates, tags, or note types while thinking.
2. **The user owns the data.** Notes remain ordinary Markdown files in an Obsidian vault and are versioned in Git.
3. **Preserve source material.** Raw brain dumps are append-only and never silently deleted or overwritten.
4. **Organize, do not manufacture work.** The product should structure and connect the user's own thoughts. It should not become an unsolicited study-guide or research-generation machine.
5. **Explainable automation.** Every automated change must be traceable to a source capture and a Git commit.
6. **Conservative writes.** Automated changes are small, reversible, and confidence-aware.
7. **Provider flexibility.** Local models do repetitive work; Claude or Codex handle selected high-reasoning work.

## 4. Primary user journey

### Capture

1. The user opens `00 Inbox/Brain Dump.md` in Obsidian on an iPhone.
2. The user uses native iPhone dictation or typing to add a thought.
3. A capture boundary marks the entry as ready to process.
4. The Obsidian Git community plugin commits and pushes the vault to a private GitHub repository.

### Curate

1. A service on the user's Linux VM detects the new Git commit, pulls the vault, and queues the capture.
2. The curator extracts topics, tasks, people, companies, projects, learning concepts, and dates.
3. GBrain retrieves related notes and graph context from the same vault.
4. The curator creates a structured plan for safe changes.
5. High-confidence changes are applied. Uncertain changes go to a review queue.
6. The curator commits and pushes the resulting Markdown changes.
7. The user pulls the changes in Obsidian and sees organized notes, links, and tasks.

### Recall and planning

The user can ask questions such as:

- What do I already know about evals?
- What have I said about this startup idea?
- What should I learn next in AI engineering?
- What is the current status of this project?
- Which people or applications do I need to follow up with?

The system retrieves relevant captures, notes, tasks, projects, and relationships, then answers with source-linked context.

## 5. Information model

### Core note types

| Type | Purpose | Examples |
|---|---|---|
| Capture | Immutable raw thought source | Voice brain dump, quick text thought |
| Project | Active or potential work with progress and next actions | AIVA, second-brain curator, homelab project |
| Learning track | A living map for a capability or field | AI Engineering, Networking, Kubernetes |
| Learning topic | A concept within a learning track | Evals, RAG, durable workflows |
| Idea | An early product or technical concept | Oil and gas workflow automation |
| Person | Contact history and follow-ups | Recruiter, mentor, founder |
| Company | Company context, roles, outreach, and applications | Cohere, Google |
| Task | Actionable work linked to related entities | Apply to a role, message a contact |
| Daily plan | Time-bound plan and task view | Today, tomorrow, weekly review |
| Reference | Durable technical notes, links, decisions, and snippets | Tool comparison, architecture decision |

### Suggested vault layout

```text
00 Inbox/
  Brain Dump.md
  Review Queue.md
  Captures/
01 Projects/
02 Learning/
  AI Engineering/
  Networking/
03 Career/
  Companies/
  People/
  Applications/
04 Ideas/
05 Tasks/
  Inbox.md
  Today.md
  This Week.md
06 Daily/
99 Archive/
```

### Shared metadata

Notes should use lightweight frontmatter where it helps querying and safe automation.

```yaml
type: learning-topic
status: queued
track: AI Engineering
aliases: [Evaluation, LLM Evals]
related_projects: [[AIVA]]
source_captures:
  - capture-2026-08-29-001
```

## 6. Learning-map behavior

Learning tracks are living maps, not rigid study guides. Each track captures:

- a capability goal;
- an ordered but editable set of learning topics;
- prerequisites or dependency relationships;
- current status for each topic;
- related projects where a topic can be applied;
- user notes, questions, resources, and tasks.

Example statuses: `curious`, `queued`, `learning`, `applying`, `retained`.

When a new brain dump mentions a relevant concept, such as evals:

1. Find the closest existing learning track, for example `AI Engineering`.
2. Determine whether the concept is a new topic, a subtopic, a task, a project connection, or a duplicate.
3. Create or update a lightweight concept note.
4. Link it to relevant projects, such as AIVA.
5. Add it to the learning map in an appropriate rough position.
6. Do not silently reorder foundational topics or produce a detailed curriculum. Major priority or dependency changes should be suggested for review.

## 7. Automated curation behavior

### Extraction

From each capture, identify:

- actionable tasks;
- dates and time references;
- projects and ideas;
- learning tracks and concepts;
- people, companies, and outreach actions;
- links to existing notes;
- possible duplicates or additions to canonical notes.

### Allowed automatic changes

- Create a new note from a repeated or substantial new concept.
- Append a sourced item to a named section of an existing note.
- Create a task and attach it to the correct project, person, company, or learning topic.
- Add an Obsidian wikilink.
- Add or update constrained frontmatter fields.
- Add an item to a learning map.
- Add uncertain proposals to `00 Inbox/Review Queue.md`.

### Disallowed automatic changes in the MVP

- Delete raw captures or existing notes.
- Rewrite whole notes.
- Rename or move notes.
- Make broad taxonomy changes.
- Change major learning-plan ordering without review.
- Send messages, submit applications, or take external actions.

## 8. Task and planning behavior

The system must support tasks as first-class items, rather than leaving actions buried in notes.

- Extract explicit and implicit actions from brain dumps.
- Interpret references such as tomorrow, this week, and before Friday.
- Maintain a persistent task inbox.
- Link each task to its relevant context.
- Support daily and weekly planning views.
- Surface overdue, unscheduled, and blocked tasks.
- Enable questions such as: What should I work on tomorrow? What follow-ups are due? What tasks relate to this project?

## 9. GBrain integration

GBrain operates on a clone of the same Markdown vault. It is not a second source of truth.

GBrain responsibilities:

- index Markdown and Obsidian wikilinks;
- provide semantic and keyword retrieval;
- maintain a richer graph of relationships;
- provide context to Claude, Codex, and local agents through MCP or a controlled API;
- run scheduled, low-risk enrichment and relationship discovery.

Heap responsibilities:

- detect completed brain dumps;
- route captures through the curation workflow;
- enforce safe write policies;
- update Markdown notes and Git history;
- maintain the review queue and processing ledger.

Obsidian responsibilities:

- mobile and desktop capture;
- reading and manual editing;
- Graph View, Canvas, search, and task views;
- Git sync through the existing community plugin.

## 10. Model routing

### Deterministic code

Use normal code for capture IDs, Git operations, queues, idempotency, date parsing where reliable, file validation, and writer locks.

### Local model on the GPU VM

Use a local 7B to 8B class model for cheap repeated work:

- extraction of tasks, topics, entities, and candidate links;
- note classification;
- duplicate detection and ranking;
- simple summaries;
- confidence scoring.

### Claude or Codex

Use selectively for higher-reasoning work:

- ambiguous merge versus create decisions;
- multi-note synthesis;
- project status and planning questions;
- weekly review;
- more nuanced learning-map suggestions.

The MVP must not depend on unlimited unattended subscription usage. Background work should use local or tightly budgeted model calls. Provider-specific authentication and pricing are implementation decisions that must remain configurable.

## 11. Reliability and safety requirements

- Private GitHub repository is the versioned source of truth.
- The VM has one working clone and serializes all automated writes.
- Every capture has a stable ID and processing status.
- Processing is idempotent: rerunning a capture must not duplicate tasks or content.
- The curator pulls before writing and pushes only fast-forward-compatible commits.
- No force pushes.
- Every generated edit cites its source capture in frontmatter or a short provenance section.
- A review queue receives low-confidence or conflicting changes.
- Model output is a structured plan, validated before Markdown files are changed.
- Local databases, caches, model settings, and credentials stay outside the vault or are ignored by Git.

## 12. Technical architecture

```text
iPhone Obsidian + native dictation
        |
Obsidian Git plugin
        |
Private GitHub repository
        |
Linux VM vault clone
        |--------------------|
Vault Curator             GBrain
        |                    |
Local model / Claude / Codex
        |
Commit and push safe Markdown changes
```

Initial infrastructure should stay minimal and debuggable:

- one Linux VM service for the curator;
- one clone of the vault;
- Git polling or a lightweight webhook later;
- GBrain with a local database;
- local model server on the existing GPU VM;
- systemd or Docker Compose for persistent operation;
- no unnecessary third-party services, accounts, or secrets.

## 13. MVP scope

### Must have

1. A single brain-dump inbox in Obsidian.
2. A clear capture boundary and stable capture IDs.
3. Git-triggered or Git-polled processing on the VM.
4. GBrain retrieval over the vault.
5. Local-model extraction of tasks, topics, entities, and related-note candidates.
6. A constrained writer that creates notes, appends sourced additions, creates tasks, and adds links.
7. A review queue for uncertain decisions.
8. Automated commits and pushes back to the vault.
9. A simple query interface for personal recall.

### Later

- Nightly global relationship enrichment.
- More advanced learning-map maintenance.
- Weekly review and planning reports.
- An Obsidian plugin or dedicated local UI.
- Visual relationship explorer beyond Obsidian Graph View.
- External integrations such as calendar, email, job boards, or read-later services.
- Multi-user or hosted deployment.

## 14. Success criteria

The MVP is successful when the user can dictate a mixed thought on an iPhone and, after sync, reliably find:

- the original capture preserved;
- extracted tasks in the task system;
- project, career, learning, and people notes updated or created correctly;
- meaningful Obsidian links added;
- ambiguous items clearly placed in a review queue;
- useful answers to questions over prior notes without manually searching through the vault.

## 15. Open decisions

- Final product name. Current strongest option: **Heap**.
- Exact capture-boundary UX in `Brain Dump.md`.
- Whether tasks use plain Markdown, Obsidian Tasks, Dataview, or a custom schema.
- Local model and embedding model selection for the GTX 1070-class GPU.
- Whether GBrain autopilot writes directly, or only suggests changes for the curator. Default recommendation: GBrain retrieves and enriches; the curator is the only writer.
- Authentication method and cost budget for unattended Claude or Codex reasoning.
- Initial query interface: CLI, MCP client, an Obsidian command, or a small local web UI.
