Back to [Evidence Studio Feedback](Evidence%20Studio%20Feedback.md) · Full citations: [References](References.md)

## How I used the research

I used Evidence's own documentation, product pages, and customer-workflow example to check the claims retained in these notes. The sources below establish documented capabilities and a reported customer example. My observations while building the project are recorded separately in [Walkthrough Details](Walkthrough%20Details.md).

## Framework and reporting

| ID | Documented point | Source (MLA in-text) |
| --- | --- | --- |
| S8 | Core is the framework powering Studio, with live warehouse queries, reusable metrics, and validation tooling. My long-term adoption thesis is an interpretation of that foundation. | (McAskill, “Evidence Core”) |
| S9 | A reusable metric definition can carry its aggregation, filter, format, and label for components to inherit. I did not test a shared-metric revision during this walkthrough. | ("Metrics") |
| S10 | Evidence components provide reporting elements with typed attributes and validation. Their existence does not guarantee that every generated report is semantically correct. | ("Components") |

## Evidence Agent and authoring

| ID | Documented point | Source (MLA in-text) |
| --- | --- | --- |
| S1 | Project `agent/` files provide always-loaded context and on-demand skills, version-controlled with the project. I noticed the directory but did not customize it. | ("Evidence Agent," Evidence Docs) |
| S2 | The CLI supports local development with an agent of your choice, with GitHub PR previews documented. I did not test the local CLI path here. | ("CLI") |
| S3 | The editor agent proposes a diff and can update project/page settings. My integration wish concerns continuity across surrounding workflows, not a lack of these capabilities. | ("Editing") |
| S4 | The Analytics Agent page describes queries/sources behind answers and prompts/implementation notes saved with insights. That does not establish a complete action trace. | ("Analytics Agent") |

## Data setup and access

| ID | Documented point | Source (MLA in-text) |
| --- | --- | --- |
| S5 | The logged-in CLI uses the Studio organization's connection, credentials, and access rules. This alone does not establish every project's effective access or hosted project-scoping options. | ("Connect Your CLI to Your Data") |
| S6 | Table and row access controls are documented separately; direct-connector users must check connector-specific rules. I did not test those controls. | ("Row Level Security") |

## Account-health example

| ID | Reported point | Source (MLA in-text) |
| --- | --- | --- |
| S7 | Evidence describes an unnamed customer refactoring an account-health dashboard into a guided skill, using product usage, support, and renewal context. This is a vendor-reported workflow, not a disclosed customer identity or measured result. The maintainer/customer-success roles in my example are my interpretation. | (McAskill, “That Dashboard”) |

## What remains a question

I did not establish whether hosted project-specific connection configuration exists, or test a complete agent-action record. The notes therefore describe what I wanted to understand and revisit; they do not claim unrestricted data access, missing permissions, or the absence of every relevant logging feature. Wider adoption, a lower learning curve, and better collaboration remain ideas to test.
