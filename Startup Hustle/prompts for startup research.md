
i want to find tech startups that are vancouver or sf based that fit my criteria. these are the startups i wil be targeting to get a job at. they should be accepting new grad / early careers in some way. i will use this info to create a 3-4 study guide. the prompt for the study guide is below. i want to do stuff with ai. 

```
Act as an experienced startup engineer and technical educator. Create a personalized 3-4 week intensive study guide to prepare me for working at a fast-paced startup. The guide must balance deep technical learning with practical business acumen, because engineers at startups need to handle ambiguity and collaborate with product and sales teams.
Target startups: I will provide the list in a follow-up message. Once provided, tailor examples, tooling, and project ideas to their industry and likely stack. If no list is provided, assume a typical B2B SaaS startup using modern JavaScript/TypeScript + Python.
Technical topics to cover (expand as needed):

Agentic AI development: building production-ready agents, not demo quality
LangChain and LangGraph: workflows, state management, tool calling
Git and version control workflows: branching, rebasing, PR reviews
Testing frameworks: pytest and Jest; unit vs integration vs E2E
Database technologies: SQL, NoSQL, ORMs, migrations, indexing basics
Hosting and deployment: Docker, CI/CD, cloud platforms (AWS/Vercel), with explicit coverage of Vercel for frontend and full-stack deployments
Complementary topics: observability, basic security, API design

Business & soft skills topics:

Startup fundamentals: business models, metrics (MRR, churn, CAC), planning
How engineers interface with product/sales: framing technical decisions in business language
Handling ambiguity: decision-making frameworks, prioritization, communication

Resource requirements per week:

Curated reading/watching materials (free or affordable) with actual links
Exact chapters or sections to study, not just "read this"
Time-boxed assignments to keep pace

Mini project requirements per week:

Technically deep and quick to build (2-3 days) using common startup technologies
Example: build a LangGraph-based support agent that retrieves from product docs, has conversational memory, and is containerized with Docker; include unit + integration tests and a GitHub Actions CI pipeline
Each project must tie back to a business goal or an ambiguous situation likely faced in a startup

Output format:

Week-by-week breakdown (Week 1, Week 2, etc.)
Each week: focus theme, resources, daily schedule (Mon-Fri), one main mini project, and one business-focused reading/task
Final section: "What to show in interviews" summarizing 3-5 portfolio pieces and talking points

Constraints:

Total time commitment: 3-4 weeks, assuming 4-6 hours of dedicated study per day
Prioritize quick wins and practical skills over theory
Use clear, actionable language and avoid fluff
Explicitly include Vercel in the deployment/hosting modules and in project setup where relevant


```


---
# AI Startup Targeting and Four-Week Readiness Sprint

Act as a senior startup researcher, hiring-market analyst, AI and backend engineer, and technical educator.

Your job is to:

1. Research and rank realistic startup employers.
2. Help me select 4 to 6 anchor companies.
3. Create a company-informed four-week study guide that uses my existing AIVA project as the main learning vehicle.

Follow the staged process below.

## 1. Interaction Flow

Complete the work in two stages.

### Stage 1: Company Research

Research, verify, classify, and rank suitable companies. Present the findings and then stop.

Ask me to approve or change the recommended set of 4 to 6 anchor companies.

### Stage 2: Study Guide

Only after I select the anchor companies, create the four-week study guide.

Do not generate a generic study guide before the anchor companies are confirmed.

## 2. Candidate Profile

I am a recent University of British Columbia graduate with a Bachelor of Science in Computer Science and Physics.

I am targeting my first long-term, full-time software engineering role. My professional evidence includes internship, contract, freelance, and substantial project work.

### Work Authorization and Location

- Canadian citizen authorized to work in Canada.
- Currently based in Calgary.
- Open to relocating to Vancouver.
- No current United States work authorization.
- Do not assume sponsorship or TN eligibility.
- Record only what employers or official job descriptions state.
- Prioritize Vancouver opportunities over San Francisco opportunities.

### Technical Experience

My current evidence includes:

- Python, TypeScript, JavaScript, SQL, React, Django REST Framework, FastAPI, Flask, Node.js, and Express.js.
- PostgreSQL, MySQL, Redis, MongoDB, Celery, Docker, GitHub Actions, Linux, AWS, REST APIs, OAuth 2.0, JWT, and RBAC.
- Production backend services, workflow automation, relational data modeling, authentication, third-party integrations, structured logging, alerts, and automated testing.
- Computer vision and physical-system automation involving laboratory equipment, sensors, device controls, real-time monitoring, and incident response.

Notable evidence from my experience:

- Built a React, TypeScript, Python, and FastAPI production automation platform that tripled protocol deployment speed and doubled weekly production yield.
- Implemented structured logging, contextual tracebacks, alerts, execution history, and incident-response tooling.
- Improved computer-vision analysis accuracy by 25 percent and increased automated data acquisition by more than 90 percent.
- Built financial and operational platforms using React, Express.js, Node.js, Python, MySQL, REST APIs, authentication, RBAC, validation, relational constraints, and audit history.
- Worked with a 4 to 5 person engineering team using sprint planning, Git workflows, pull requests, reviews, documentation, and delivery prioritization.

### Existing AI Project

I have an Agentic Productivity Platform called AIVA.

Current AIVA evidence includes:

- Python and Django REST Framework backend.
- OpenAI API integration.
- 60 registered tools and actions.
- Multi-step workflows across email, calendars, contacts, cloud storage, and Notion.
- Seven OAuth 2.0 integrations.
- Thirty-four authenticated API routes.
- Celery scheduling and background processing.
- Retries, backoff, token refresh, and rate-limit handling.
- A 256-test backend suite, with more than half written by me.
- Thirty-one security-focused unit and API tests.

AIVA is substantial, but I do not yet consider these areas production-ready:

- Agent architecture and evaluations.
- Cloud deployment and CI/CD.
- Observability and reliability.
- Database design and performance.
- Security and data protection.
- Product experience and validation with real users.

My longer-term idea is to make AIVA a reusable platform with core capabilities that can be configured or extended for different industries.

Treat that as a hypothesis to evaluate, not a final architecture decision.

The study guide should prepare me to make those decisions. A separate repository-specific discussion will later produce the detailed AIVA productionization plan.

## 3. Target Engineering Work

Prioritize companies and roles involving or adjacent to:

- Production AI agents and workflows.
- AI infrastructure and developer platforms.
- Applied AI product engineering.
- Backend and platform engineering at AI-native companies.
- B2B agents and workflow automation.
- Developer tools and AI infrastructure.
- Data, search, retrieval, and research products.
- Vertical AI, especially health, biotechnology, security, and operational software.

A role does not need “AI” in its title.

General backend, platform, infrastructure, product, or full-stack software roles qualify when the company itself is genuinely AI-native.

Rank backend, platform, infrastructure, and backend-heavy product work above frontend-heavy work.

Exclude:

- Frontend-only opportunities when no meaningful backend or platform ownership exists.
- Pure research positions requiring a master's degree, PhD, or publication record.
- Senior, staff, principal, lead, manager, director, or architect positions.
- Founding-engineer roles.
- Roles that clearly require more than two years of professional experience unless they are explicitly designated as new graduate or early career.

## 4. Company-Stage Gate

The primary company pool must contain private, product-focused startups at Series B or later.

Qualifying stages include:

- Series B.
- Series C.
- Series D.
- Series E or later.
- Late-stage private or pre-IPO companies that still operate as technology startups.

Do not include:

- Pre-seed companies.
- Seed-stage companies.
- Series A companies.
- Accelerators or incubators as employers.
- Agencies, consultancies, staffing firms, or outsourcing companies.
- Public companies unless I explicitly approve them later.
- Companies whose only relevant opportunity is a founding-engineer role.

Exclude OnDeck AI because it is below the required company stage, even though its technical work otherwise aligns with my background.

Do not weaken the Series B-or-later gate merely to produce a longer list.

Report the company’s latest verified funding round, the announcement date, and the source. If the stage cannot be verified, place the company in an “Unverified Stage” section rather than the qualified shortlist.

## 5. Geographic Search Tiers

Keep the following pools separate.

### Tier 1: Primary Vancouver Targets

Series B-or-later AI-native companies that:

- Are headquartered in Metro Vancouver, or
- Have a meaningful engineering office or team in Metro Vancouver.

These should receive the highest ranking priority.

### Tier 2: San Francisco Targets

Series B-or-later AI-native companies headquartered in or meaningfully based in the San Francisco Bay Area.

Divide these companies into:

1. Can hire in Canada.
2. Explicitly supports relevant United States work authorization.
3. High-fit networking target, but work authorization or hiring feasibility is unclear.

Do not imply that a San Francisco role is immediately actionable when authorization is unresolved.

### Fallback A: Vancouver AI-Heavy Startups

Series B-or-later Vancouver startups that are not fully AI-native but have:

- A major AI product line.
- Substantial production AI engineering.
- AI infrastructure or agent development.
- Relevant backend or platform roles supporting AI products.

Label these separately from AI-native companies.

### Fallback B: Canada-Remote AI-Native Startups

Series B-or-later AI-native companies based elsewhere that explicitly hire software engineers remotely in Canada.

Label these separately and rank them below qualifying Vancouver companies.

Do not mix fallback companies into the primary Vancouver list.

## 6. Early-Career Eligibility Gate

A current opportunity qualifies when at least one condition is verified:

- The title explicitly says new graduate, early career, entry level, junior, associate, Engineer I, SWE I, or an equivalent label.
- No minimum professional experience is stated.
- The position accepts 0 to 2 years of experience.
- The description explicitly counts internships, projects, research, contract work, freelance work, or equivalent experience.
- The company has an official apprenticeship, residency, rotational program, or recurring early-career program open to recent graduates.

Classify each company as:

### Apply Now

A live, relevant, early-career-accessible opportunity is verified and the work location appears actionable.

### Active Outreach

No immediately eligible role is open, but the company has recent or recurring evidence of hiring early-career engineers.

### Network and Monitor

The company is an excellent technical fit, but there is no current evidence of an accessible early-career opening.

Do not describe historical hiring evidence as a current opening.

If few companies meet the criteria, return a shorter list instead of padding it with unsuitable employers.

## 7. Research Standards

Use current web research and state the research date.

Prioritize:

1. Official company websites.
2. Official career pages.
3. Official Ashby, Greenhouse, Lever, or company-hosted job descriptions.
4. Official engineering blogs and documentation.
5. Official GitHub organizations.
6. Official funding announcements.
7. Reliable technology publications or funding databases when primary funding information is unavailable.

For every shortlisted company:

- Verify that the company is still active.
- Verify its funding stage.
- Verify its Vancouver, San Francisco, or Canadian-remote presence.
- Open every job link and confirm it is still active.
- Record posting dates when available.
- Write “not stated” when a date or requirement is unavailable.
- Distinguish verified facts from inferences.
- Link directly to the evidence.
- Do not infer sponsorship, remote eligibility, hiring plans, technologies, or early-career access.
- Do not rely on generic job aggregators when an official posting is available.
- Mark unresolved information as unknown.

## 8. Company Scoring

Apply all hard gates before scoring.

Score each qualifying company out of 100:

- Early-career accessibility: 25 points.
- Vancouver or actionable Canadian location fit: 20 points.
- AI-native product alignment: 20 points.
- Backend, platform, infrastructure, or applied-AI alignment: 15 points.
- Engineering maturity and likely mentorship capacity: 10 points.
- Relevance to my current experience and AIVA development: 10 points.

Assign a separate evidence-confidence rating:

- High.
- Medium.
- Low.

Do not allow a high aggregate score to conceal:

- Work-authorization problems.
- Missing early-career evidence.
- An unverified funding stage.
- A seniority mismatch.
- A lack of meaningful engineering presence in the stated location.

## 9. Althra Network Leverage

I have personally spoken with the founder of Althra, a Vancouver startup incubator.

Do not treat Althra itself as a target employer.

Do not include its cohort companies unless they independently satisfy the Series B-or-later gate.

Instead, treat this relationship as an ecosystem advantage.

After producing the shortlist, include:

- Which shortlisted Vancouver companies or categories may be appropriate to ask him about.
- Three high-value questions I could ask about Vancouver’s growth-stage AI ecosystem.
- A non-transactional way to ask for perspective or selected introductions.
- Which companies should be researched further before requesting an introduction.
- A warning against asking for broad or poorly targeted introductions.

Do not assume that this connection guarantees an introduction, endorsement, or hiring access.

## 10. Stage 1 Output

Produce the following sections.

### A. Research Scope and Assumptions

State:

- Research date.
- Geographic definitions.
- Company-stage definition.
- AI-native definition.
- Early-career eligibility rules.
- Important limitations.

### B. Search Funnel

Report:

- Number of companies initially considered.
- Number excluded by stage.
- Number excluded by geography.
- Number excluded by weak AI alignment.
- Number excluded by seniority or experience requirements.
- Number remaining in each geographic tier.

### C. Ranked Company Tables

Create separate tables for:

1. Primary Vancouver targets.
2. San Francisco targets.
3. Vancouver AI-heavy fallback companies.
4. Canada-remote AI-native fallback companies.

For each company include:

- Company and official website.
- Location evidence.
- Latest verified funding stage and date.
- Product and primary customer.
- Why the company is AI-native or AI-heavy.
- Approximate company or engineering-team size when reliably available.
- Relevant engineering role families.
- Current eligible role, if any.
- Early-career evidence.
- Work-location and authorization status.
- Verified technical-stack signals.
- Apply Now, Active Outreach, or Network and Monitor.
- Fit score.
- Evidence confidence.
- Direct supporting sources.

### D. Top-Company Briefs

For the strongest companies, explain:

- Why the company fits my goals.
- What I could plausibly work on.
- Which conclusions are verified and which are inferred.
- My strongest matching experience.
- My most important gap.
- The portfolio evidence that would strengthen my candidacy.
- The best immediate action.

### E. Cross-Company Skill Matrix

For each recurring skill or technology, include:

- Companies providing evidence for it.
- Number of target companies mentioning it.
- Whether the evidence is explicit or inferred.
- My existing evidence.
- Gap severity.
- Recommended priority.

Separate:

- Skills common across the target set.
- Skills unique to one company.
- Technologies that are fashionable but not supported by target-company evidence.

### F. Excluded and Unverified Companies

Briefly explain notable exclusions, including OnDeck AI.

### G. Recommended Anchor Set

Recommend 4 to 6 anchor companies.

Favor:

- Vancouver companies.
- Current or credible early-career access.
- Strong AI-native alignment.
- Engineering maturity.
- Overlap with production agents, AI infrastructure, applied AI, backend, or platform work.

Then stop and ask me to accept, remove, or replace companies.

Do not generate Stage 2 until I respond.

## 11. Stage 2 Study-Guide Requirements

After I confirm the anchor companies, re-check time-sensitive job information and create a four-week plan.

Schedule:

- Four weeks.
- Monday through Friday.
- Four to six hours per day.
- Twenty to thirty hours per week.
- Eighty to one hundred twenty total hours.
- Weekends may be optional buffers but cannot be required.
- At least 60 percent of the scheduled time should be hands-on.
- Reading and watching should normally remain under 90 minutes per day.

Every daily assignment must specify:

- Time allocation.
- Learning objective.
- Resource.
- Hands-on task.
- Concrete artifact.
- Completion check.

Do not use vague tasks such as “learn databases” or “continue working on AIVA.”

## 12. Evidence-Driven Curriculum Selection

Let the confirmed anchor companies determine the largest new technical investment.

Do not add Go, Rust, Kubernetes, Terraform, or another major technology merely because it is popular.

Treat a technology as a core topic when:

- Multiple anchor companies explicitly use or request it, or
- It addresses a critical AIVA production gap and is broadly relevant to the selected roles.

Otherwise, place it in a company-specific elective.

Use Python and TypeScript as the default implementation languages unless the evidence strongly supports another choice.

Explain why every major topic is:

- Core.
- Elective.
- Deferred.

## 13. Required Technical Coverage

Tailor the depth and order to the anchor companies while covering:

### Production AI

- Model APIs and structured outputs.
- Tool calling and workflow orchestration.
- Agent state and memory.
- Human approval boundaries.
- Retrieval when justified.
- LangChain and LangGraph, including when not to use them.
- Direct SDK versus framework tradeoffs.
- Evaluation datasets and scoring rubrics.
- Regression testing and failure taxonomies.
- Prompt and model versioning.
- Hallucinations, prompt injection, unsafe tool use, and tool failures.
- Latency, cost, reliability, and quality tradeoffs.
- AI observability and production debugging.

### Backend and Data

- API design and error contracts.
- Authentication and authorization.
- Relational modeling and ORM tradeoffs.
- Database migrations and constraints.
- Indexes and query plans.
- SQL, NoSQL, and vector-storage tradeoffs.
- Background jobs and queues.
- Retries, backoff, timeouts, rate limits, and idempotency.
- Caching and performance measurement.

### Platform and Reliability

- System-design fundamentals.
- Failure-mode analysis.
- Structured logs, traces, metrics, and alerts.
- Health checks and graceful degradation.
- Runbooks and incident response.
- Secrets management and least privilege.
- Tenant and data isolation.
- Threat modeling and security testing.

### Testing and Collaboration

- pytest and Jest.
- Unit, integration, contract, end-to-end, and AI-evaluation testing.
- Deterministic model mocks and fixtures.
- Git branches, commits, rebasing, merge conflicts, and pull requests.
- Code-review checklists.
- Architecture decision records.
- GitHub Actions and CI/CD.

### Deployment

- Docker and reproducible development environments.
- Cloud architecture based on target-company evidence.
- AWS fundamentals where relevant.
- Vercel frontend deployments and preview environments.
- Vercel full-stack and serverless patterns.
- Vercel limitations for long-running, stateful, queued, or streaming AI workloads.
- A justified decision about which components belong on Vercel.
- Deployment verification, monitoring, rollbacks, and incident recovery.

## 14. AIVA as the Learning Vehicle

Do not recommend rebuilding AIVA from scratch.

Use the four weeks to strengthen selected production capabilities and produce decision-making evidence.

The guide should examine whether AIVA should become:

1. A configurable SaaS product.
2. A reusable agent platform or SDK.
3. A shared core with industry-specific modules.
4. Another architecture supported by clearer evidence.

Do not choose an architecture without explaining the product, operational, security, and maintenance tradeoffs.

Possible reusable core capabilities to evaluate include:

- Authentication and tenant management.
- Tool and integration registry.
- Workflow orchestration.
- Scheduling and background jobs.
- OAuth and credential management.
- Evaluation and regression infrastructure.
- Observability and audit history.
- Permissions and policy enforcement.
- Configuration and extension interfaces.

Possible vertical-specific layers include:

- Industry integrations.
- Domain data models.
- Specialized workflows.
- Prompts and evaluation cases.
- Compliance and permission rules.
- User-facing configurations.

Treat these as design hypotheses, not predetermined requirements.

Each week should produce one shippable AIVA-related milestone or prototype. Clearly distinguish:

- Required work.
- Stretch work.
- Repository-dependent work that requires a later code audit.
- Explicit non-goals.

## 15. Business and Communication Coverage

Include practical assignments covering:

- Startup business models and customer segments.
- MRR, ARR, activation, churn, retention, CAC, LTV, and gross margin.
- AI inference cost and cost per successful task.
- Customer discovery and problem validation.
- Translating technical decisions into customer, revenue, risk, and delivery effects.
- Working with product and sales.
- Scoping under uncertainty.
- Writing short tradeoff memos and decision records.
- Delivering a five-minute product demonstration.
- Responding to customer and technical objections.

Connect every business task to AIVA or an anchor company.

## 16. Resource Standards

For every resource:

- Provide a working link.
- Name the exact chapter, page, module, or heading.
- Mark it Required or Optional.
- Estimate the time.
- Explain the artifact or skill it supports.
- Prefer primary documentation and strong engineering material.
- Ensure the core plan can be completed for free.
- State the price of any optional paid resource.
- Do not invent chapter or section names.
- Do not provide resources that are not used in the schedule.

## 17. Weekly Output Format

For each week include:

1. Focus theme.
2. Why it matters to the anchor companies.
3. Learning outcomes.
4. Required and optional resources.
5. Monday-to-Friday schedule.
6. AIVA milestone.
7. Acceptance criteria.
8. Required tests.
9. Business or communication assignment.
10. Definition of done.
11. Total estimated hours.

## 18. Final Study-Guide Sections

Include:

### Company-to-Skill Traceability

Map each major topic to evidence from the anchor companies.

### What to Show in Interviews

Identify 3 to 5 portfolio artifacts and explain:

- What each artifact proves.
- Which companies it supports.
- Which decisions I should be prepared to defend.
- Which failure or reliability story I can discuss.
- How to explain the business value before implementation details.

### Company-Specific Talking Points

Connect my existing experience, AIVA improvements, and the company’s likely engineering problems.

### AIVA Productionization Handoff

Create a compact handoff for the separate AIVA productionization discussion containing:

- Current evidence.
- Known gaps.
- Architecture hypotheses.
- Decisions that require a repository audit.
- Highest-risk unknowns.
- Recommended validation experiments.
- Candidate production milestones.
- Questions that should be answered before implementation.

Do not pretend that the study guide itself is a complete productionization specification.

## 19. Final Quality Checks

Before returning either stage, verify that:

- Every primary company is Series B or later.
- OnDeck AI is excluded.
- Vancouver is prioritized.
- Fallback pools are clearly separated.
- Job and company claims are current and linked.
- Early-career access is supported by evidence.
- Work-authorization uncertainty is explicit.
- Facts and inferences are distinguishable.
- The curriculum follows target-company evidence.
- The schedule fits four to six hours per weekday.
- AIVA is extended rather than unnecessarily rebuilt.
- The plan prepares a later productionization discussion without fabricating repository details.
- The output is direct, actionable, and free of filler.