# Heap — Brain-Dump App

[[Projects & Learning/Projects/Project Index|Projects]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Outcome

Build an Obsidian-first organization system for people who learn and build things: capture a brain dump without filing it, then organize its ideas, projects, learning, and tasks into a connected workspace.

**Working name:** Heap. **Stage:** concept and proposed MVP; no implementation is claimed here.

## Core idea

The original idea was a second brain combining Obsidian with an AI assistant: brain dump freely and let it organize thoughts. The more detailed proposal adds mobile voice/text capture, preserved raw entries, Git history, context retrieval, conservative note updates, a review queue, and source-linked recall.

Obsidian remains the writing/browsing interface, and Markdown remains the source of truth. A curator running on a VM would process completed captures, link relevant notes, and commit small updates. GBrain is a proposed retrieval component whose fit still needs checking.

## Detailed design

[[Projects & Learning/Projects/Heap/Product Spec|Product Spec]] contains the imported product concept, workflows, information model, reliability requirements, proposed architecture, MVP, and open decisions. It has been revised to use a budgeted hosted AI choice rather than requiring a dedicated model server. Provider, retrieval tooling, and final stack are undecided.

## Connections

- [[Projects & Learning/Start Here|This planning workspace]] is a practical example of the organization workflow the app should support.
- [[Projects & Learning/HomeLab/Remote Development/Remote Development|Remote Development]] provides a potential development/service environment.
- [[Projects & Learning/HomeLab/Shared MCP Servers/Shared MCP Servers|Shared MCP Servers]] may connect retrieval and curation tools to agents.
- [[Projects & Learning/HomeLab/Project Hosting/Project Hosting|Project Hosting]] supports a future interface or demo.
- [[Projects & Learning/Learning/Agents and MCP/Agents and MCP|Agents and MCP]] covers related integration concepts.

## Tasks

![[Projects & Learning/Projects/Heap/Tasks]]
