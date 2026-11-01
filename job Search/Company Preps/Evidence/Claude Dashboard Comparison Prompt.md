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
