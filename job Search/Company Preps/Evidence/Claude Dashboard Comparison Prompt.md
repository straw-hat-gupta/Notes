# Claude dashboard comparison prompt

Prepared: 2026-10-31.  
Context and observations: [[Home Lab Analytics - Review Log]].

## Prompt to paste into Claude after connecting the Evidence Studio MCP

```text
Use the Evidence Studio MCP to create a new page under Pages named Home Lab_Claude.md. Leave the existing pages unchanged, and build this independently without reading or copying the existing homelab dashboard.

I want a live dashboard showing analytics from my homelab. My data is stored in Neon, and I've already added a direct Postgres connector in Evidence Studio.

This will be my primary dashboard for seeing my homelab's status, health, and loads. I want it to update every second. I've increased how often the collector sends data to Neon and recently added more data.

Inspect the connected data yourself to decide what to show. Include a status banner, node health grids, a pipeline health section, and temperature components using whatever temperature information is available. Suggest any other useful additions based on the data, and explain any assumptions or limitations.
```

## Comparison boundaries

This consolidates user-provided goals and later component requests from several Studio-agent turns into one prompt. It deliberately omits discovered schema/table names, node/sensor counts, sensor status, observed collection cadences, generated SQL, previous errors, and fixes. It also omits network/storage/service categories from the retrospective discovery description.

This compares the native Studio agent with Claude accessing the same platform through MCP. It is not a comparison against building without Evidence, and it does not isolate model capability from tool/context differences. The data and available telemetry may have changed since the original run. Record connection/setup effort, exact Claude model if known, interventions, output, errors, and task completion. No Claude connection or run has been verified here.

## Product-feedback logging add-on

```text
While building this dashboard, keep product-review notes in my Obsidian vault. Record meaningful pain points, incompatibilities, confusing behavior, missing capabilities, documentation mismatches, and especially useful interactions as they occur.

Folder:
/Users/samgupta/brain/Notes/job Search/Company Preps/Evidence/

Use Product Review Plan.md for the review questions. Save observations in Home Lab Analytics - Review Log.md, alongside the existing notes. To preserve the independent build, inspect only the log's structure and entry headings before your first build; do not use the earlier agent's findings to design your dashboard.

For each meaningful observation, record:
- Date, Claude/MCP context, and task/step.
- What you attempted, expected, and actually observed; include exact relevant errors or tool responses without secrets.
- Impact: blocked work, extra steps, confusion, or time lost.
- Any workaround, retry, or resolution, preserving the original experience.
- Connections to the relevant review questions: Evidence's value, Studio versus open source, collaboration, usability, customer use cases, or alternatives.
- A separately labeled interpretation and possible improvement, where supported.

Distinguish your observations from mine, and facts from hypotheses. Separate Evidence/Studio issues, MCP limitations, environment/setup problems, your own mistakes, and unknown causes. Do not claim a feature is missing merely because you cannot find it or your tools cannot access it.

Follow the existing entry style and use the next available HLA number. Add entries before Emerging patterns, preserve existing content, and link related notes when appropriate. After the independent first build, you may compare with earlier observations and update the synthesis without erasing history.

Continue the dashboard work while taking notes. If you cannot access the vault, keep the notes in chat and explicitly say they were not saved to Obsidian. At the end, summarize the findings and report the exact file updated.
```
