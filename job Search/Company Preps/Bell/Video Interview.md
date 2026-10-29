

questions:

consists of mostly behavioral questions. You are given only one attempt for each question. I think

there are 4-5 such questions. The maximum you can speak for every question is 2 minutes.

Why do you want to join Bell and which position, what was a diﬃcult project, and have you had

conﬂict with team members and how did you manage it?

"why are you excited for a career at Bell", "what led you to choosing the Bell graduate program", and

"why would you be a good ﬁt for this role"

Why do you want to join Bell and which position, what was a diﬃcult project, and have you had

conﬂict with team members and how did you manage it?

- What excites you about the opportunity to launch your career at Bell?
    
- What specifically drew you to our intern/graduate program, and why should we choose you for the role within the program?
    
- When have you used AI to solve a problem? What happened?
    
- Describe a recent accomplishment that you are proud of. What did you achieve and what steps did you take that allowed you to reach this accomplishment?

Why bell:
- chance to build ai tools that people actually use at a scale where reliability really matter
- Bell AI fabric ai infra canada = allows more canadian companies to take advantage of AI while staying compliant
- Ive worked on building AI tools myself as well. 
	- getting an agent to produce useful answers is only part of the challenge
	- you also have to make sure its tool calls, permissions, and multistep exectutions observable and dependable
	- makes me very interested in the engineering behind ai applications that run at the scale bell operates at
- bells graduate role brings all that together
	- im excited to help build, test, and scale AI applications at bell 
	- while learning from more experienced engs at an organization as impactful as bell
	

tell me about yourself:
- past schooling
- complex problems break them and work on tools/products that people use
- lux bio - full stack lab automation platform, first dev to lead
- wealth management - working with clients gather reqs
- agentic plat form 
- past exp made me more interested in bells roation program. 
	- useful data in to a system
	- making application reliable
	- checking what works for users
	- thats why data engineering and ml engineering appleas to me

I’ve written the first seven with a **STAR-C ending**: the story leads to a result, then the final sentence connects it to Bell. For the motivation and introduction questions, the story is lighter, but the Bell connection is still explicit.

Bell’s posting confirms the 24-month rotation and work on production AI and data systems. Bell describes AI Fabric as Canadian-hosted infrastructure for organizations with data residency needs. [jobs.bce.ca](https://jobs.bce.ca/bell/job/Verdun-2027-Graduate-Program%2C-Technology-Services-Emerging-AI-and-Data-Solutions-QC/1431592500/?utm_source=chatgpt.com)

## 1. What excites you about starting your career at Bell?

**Best angle:** AI tools people use, supported by Canadian AI infrastructure.

What excites me about Bell is the chance to build AI tools that people actually use, at a scale where reliability really matters. I’m also interested in Bell AI Fabric. Having more AI infrastructure in Canada gives organizations a way to work with sensitive data while meeting their data residency needs, and I think that’s important for wider AI adoption here.

I’ve seen a smaller version of the product challenge in an agent platform I built. Getting an agent to produce a useful answer was only one part of it. I also had to make its tool calls, permissions, and multi-step execution dependable. That made me interested in the engineering behind AI applications that can run in production.

Bell’s graduate role brings those interests together. I’d be excited to help build, test, and scale AI applications while learning how they work within a large organization.

**Recall:** Bell AI tools → Canadian infrastructure → agent platform lesson → production AI at Bell.  
**Backup angle:** Bell Cyber’s use of AI to support threat investigators, if you want an example of an application Bell has put into production. [explore.business.bell.ca](https://explore.business.bell.ca/news-and-events/bell-cyber-and-cohere-deploy-sovereign-ai-for-canadian-cybersecurity-operations?utm_source=chatgpt.com)

## 2. What drew you to this graduate program, and why should Bell choose you?

**Best angle:** Explore ML engineering and data engineering while contributing experience in systems that move data and execute AI workflows.

I’m drawn to this program because I’m especially interested in machine learning engineering and data engineering, and I want to understand how they fit together in production. A model or agent needs dependable data and a system around it to be useful. The rotation would let me work in both areas, learn from experienced people, and contribute to projects with real users.

I’d bring experience building those supporting systems. At Lux Bio, I built Python pipelines that turned equipment readings and images into usable data. More recently, I built an agent platform with about 60 tools and a separate execution pipeline for multi-step tasks. Across both projects, I had to break a large problem into parts, learn unfamiliar technology quickly, and test how the parts worked together.

I think that combination would let me contribute early at Bell while growing into the kind of engineer who can take an AI application from an idea into dependable use.

**Recall:** ML engineering plus data engineering → why rotation → Lux data pipelines and agent platform → contribute and grow.  
**Backup example:** Your Python ingestion and ETL work at TAK Softwares, if they ask you to focus more heavily on data engineering.

## 3. What skills and experience would you bring to the role?

**Best angle:** Breaking down systems, learning quickly, and translating a real need into working software.

The first skill I’d bring is breaking a complicated problem into parts I can build and test. In my AI agent project, I separated planning from execution. The planner could identify which steps needed reasoning and which were straightforward tool calls, while a separate executor carried out the plan. That made it easier to inspect failures and test the system.

I also learn new technology quickly when a problem calls for it. At Lux Bio, I had never worked with OCR or image processing. I learned enough to build a Raspberry Pi camera pipeline that read measurements from an equipment screen and made that data available to our software.

Finally, I’m comfortable working out what users actually need. For a wealth management client, I interviewed and shadowed future users before building their workflows. Those experiences fit Bell’s need for someone who can work across data, AI, and the business problem behind them.

**Recall:** Break down problems → planner and executor → learn OCR quickly → understand users and connect to Bell.  
**Backup example:** Your TAK Softwares ingestion pipelines and work with a small engineering team.

## 4. Tell us about a time you used AI to solve a problem. What happened?

**Best story:** Your agent platform. This lets you explain your own engineering judgment as well as the AI component.

I built an agent platform to solve a problem I kept running into with AI tools: they could propose a multi-step task, but carrying it out consistently across different services was harder. One example is a request to summarize emails, send the summary, and add a calendar event if the emails call for one.

I built a planner agent that breaks the request into steps. It identifies straightforward actions, such as reading email through a tool, and steps that need reasoning, such as deciding what belongs in the summary. I then built a separate, non-AI executor to run the planned tool calls through MCP servers. Keeping that execution path explicit made it easier for me to inspect what happened and handle failures.

I checked complete results against existing evaluations and tested both the backend and full task flows. The platform now supports about 60 tools. That experience is directly relevant to Bell’s goal of building and testing production generative AI applications: the quality of the answer matters, and so does whether the whole task runs correctly.

**Recall:** Inconsistent multi-step tasks → planner plus non-AI executor → evaluations and tests → production AI at Bell.  
**Backup example:** The Lux Bio image processing and OCR pipeline. Be clear that you applied OCR technology; you did not train a new model.

## 5. Describe a recent accomplishment you are proud of. What did you do to achieve it?

**Best story:** The wealth management platform, with the discovery work as the central challenge.

I’m proud of a platform I’ve been building for a wealth management client this year. They wanted to move several client and event workflows out of spreadsheets, but the hardest part at first was working out what the software needed to preserve from their day-to-day process.

I interviewed the people who would use it and shadowed how they worked. I noticed that their spreadsheets held notes about individual clients alongside the structured information. Those notes were part of how they remembered context and followed up, so I added a way to keep notes with each client in the new platform. I also worked through the data model, validation, duplicate prevention, and audit history needed for financial records.

I delivered six workflows covering areas such as onboarding, investments, transfers, and client management. I’m proud of the way I got there: I took time to understand the work before deciding what to build. That’s the same approach I’d take when translating a Bell team’s business need into a data or AI system.

**Recall:** Spreadsheet replacement → interviews and shadowing → discovered client notes → six workflows and Bell connection.  
**Backup example:** Your agent platform, particularly building and testing the execution pipeline.

## 6. Tell us about a time you showed initiative.

**Best story:** The Lux Bio pump timer that grew into production automation.

At Lux Bio, my manager initially asked me to automate a small pump so it would run on a timer. As I learned how production worked, I saw that the pump was one of many manual steps slowing down each new protocol. People also had to set up and calibrate different devices.

I started with the requested automation, then built out a system that could coordinate the equipment and give operators a dedicated interface. They could manage device settings, calibrate equipment, set up protocols, and see live measurements from one place. I built the Python services behind it and the React interface, then supported the system as it was used in production.

The finished system helped triple the speed of deploying protocols, and weekly production yield doubled. What I took from that experience is to pay attention to the work around an assigned task. At Bell, I’d bring that same habit to finding the bottleneck in a data or AI workflow and following an improvement through to a usable result.

**Recall:** Pump timer request → spotted wider manual bottleneck → built coordinated system and interface → production result and Bell connection.  
**Backup example:** Adding safeguards and monitoring after a Lux Bio production incident, if you want an initiative story centred on reliability.

## 7. Tell us about yourself.

**Best angle:** A short path from your degree to data systems and AI engineering.

I’m Smarth Gupta. I graduated from UBC in May with a combined major in Computer Science and Physics. I enjoy taking a complicated problem, breaking it down, and building something people can use.

At Lux Bio, I built software that automated lab equipment and collected production data. That work combined Python services, a React interface, and image processing. More recently, I’ve built a platform for a wealth management client, where I started by interviewing users to understand their workflows. I’ve also been building an AI agent platform that plans and carries out tasks across tools like email and calendars.

Those projects have made me especially interested in the engineering that supports AI: getting useful data into a system, making the application reliable, and checking that it works for its users. That’s why Bell’s rotation across data engineering and machine learning engineering appeals to me.

