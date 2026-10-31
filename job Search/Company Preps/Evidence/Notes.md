


questions to ask
Evidence’s code-based approach seems like a natural fit for AI agents creating reports and analytics. Was AI part of the original vision, or did that opportunity emerge as the technology became more capable?

What have you had to rethink in the framework now that agents are doing more of the work of creating and maintaining analytics?

I noticed you moved from associate to director in data science at Birch Hill quite quickly. What do you think helped you grow into that level of responsibility?

Which of those skills have been most useful in building Evidence, and what have you had to learn along the way?




questions to prep:

who are first customers you would talk and what do you want to learn from them?

if you could any question about our companies data what would you ask and how would you use that to create your product strategy

what is the first thing you would improve about our product when you join our team


they wanna know you can take all your past experiences and be able to translate that into a strong plan to succeed on the team. And that you have good intuition about what info to get and what to do with that information.


Set up this app on Neon.
1. `npm i -g neon@latest`. If that fails, use `npx neon@latest` in place of `neon`.
   If a neon command opens a browser sign-in, tell me to finish it there. If that times out or fails, ask me to run `neon login`, then retry.
2. In the project root:
   neon init -y --org-id org-little-term-34522111 --project-id raspy-block-46645064 --branch production --services postgres
3. `neon deploy`. It provisions the services in neon.ts and pulls their env vars into `.env.local` (or `.env` if it exists).
4. Wire each service into the app's code using those env vars. Consult the installed Neon agent skills for best practices, e.g., what database driver to use given the app architecture and hosting runtime.
5. Prove it works: `npm run build` must pass, then start the app, each wired service must be tested to prove it works end to end.
6. Report what changed, the command output that proves step 5, and anything that failed.