# Client Management — Working Notes

[[Projects & Learning/Projects/Client Management/Client Management|Client Management]] · [[Projects & Learning/Projects/Client Management/Source Map|Reference index]]

Preserved project reference material. Historical questions, prompts, and decisions below may need reconciling with current work. The complete source text is retained here.

---


### Context budget rules

Apply these rules to every agent session:

1. Start with the exact change ID and one concrete task.
    
2. Load the active change artifacts.
    
3. Load only the canonical capability specs that the change touches.
    
4. Load only referenced ADRs or security rules.
    
5. Inspect only the relevant implementation surface.
    
6. Start a fresh session for specification challenge, implementation, and final review.

For a read-only Claude review session:

```
claude --permission-mode plan
```

For a formal read-only Codex review:

```
codex --sandbox read-only --ask-for-approval never
```

- codex project setting i did not disable web search like gpt reccomended
Work, Referrals, Households, Appreciation, Events, COIs, Tasks, Reports, and Associates
pages needed for sure

Referrals, Households, events, COIS, and Associates
dont understand the difference between work and tasks
and reports should be upon request only
i dont understand the appreciation page
