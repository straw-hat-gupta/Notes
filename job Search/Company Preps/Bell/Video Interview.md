

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

These are written to sound natural aloud and fit within Bell’s 90-second answer limit. Each ends by connecting your experience to the role.

## 1. What excites you about starting your career at Bell?

What excites me about Bell is the chance to build AI tools that people actually use, at a scale where reliability matters. Bell AI Fabric also caught my attention. I think Canadian AI infrastructure is important because it gives more organizations a way to use AI while keeping sensitive data in Canada.

I’ve been building an agent platform myself, and it’s taught me how much work sits behind a useful AI response. The agent needs to call the right tools, respect permissions, and carry out a series of steps in a way you can inspect when something goes wrong. Those are the problems I find interesting.

This graduate role brings that interest together with the chance to learn from experienced engineers. I’d be excited to help Bell build, test, and scale AI applications that people can depend on.

## 2. What drew you to this graduate program, and why should Bell choose you?

I’m drawn to the program because I’m especially interested in machine learning engineering and data engineering. I want to understand the whole path from getting data into a usable form to building an AI application around it and keeping that application working. The rotation would let me explore both areas through real projects, with people who have experience doing this at Bell’s scale.

I’d bring hands-on experience to that learning. At Lux Bio, I built Python pipelines to collect and process data from lab equipment and images. In my own agent platform, I built the tools and execution pipeline behind multi-step AI tasks.

I’ve also learned that I can become useful quickly in a field I’m new to by asking good questions and breaking the problem down. I’d bring that approach to each placement and contribute while I’m learning.

## 3. What skills and experience would you bring to the role?

I’d bring the ability to break down a complicated problem and work through the pieces carefully. In my agent platform, I separated the part that plans a task from the part that executes it. That let me test the tool calls and see where a task failed.

I’m also comfortable learning something new when the problem requires it. My first project at Lux Bio involved reading measurements from an equipment screen with a Raspberry Pi camera. I had never used image processing or OCR before, so I learned them and built a pipeline that made those readings available to our software.

The other skill I’d bring is working with people outside engineering. For a wealth management client, I interviewed and shadowed users before deciding what to build. Bell’s role needs that combination: understanding the people and the problem, then building and testing the technical solution.

## 4. Tell us about a time you used AI to solve a problem. What happened?

I built an AI agent platform because I wanted it to carry out multi-step requests consistently across services like email and calendars. For example, someone might ask it to summarize their emails, send them the summary, and add a calendar event if one of those emails calls for it.

I built a planner agent that turns the request into steps. Some are direct tool actions, like reading an email, while others need reasoning, like deciding what belongs in the summary. I then built a separate, non-AI executor that follows the plan and calls the appropriate MCP tools.

To check the work, I compared complete results against existing evaluations and tested both backend behaviour and end-to-end tasks. The platform supports about 60 tools, and I can inspect its execution history when a step fails. That project showed me why production AI engineering has to cover the entire workflow, which is the part of Bell’s role I’m eager to work on.

## 5. Describe a recent accomplishment you are proud of.

I’m proud of a client management platform I built for a wealth management firm. They were using separate spreadsheets to track clients, referrals, tasks, and events. Information was duplicated between files, and people spent time keeping everything consistent.

They wanted a better system, but there wasn’t a complete specification. I started by interviewing the people who would use it, then shadowed them as they worked. That showed me how the information connected and where work was being repeated. I also noticed that they kept useful notes about individual clients in the spreadsheets, so I made sure those notes had a place in the new platform.

I used what I learned to define the requirements and built six workflows in React and TypeScript. The platform replaced the spreadsheet-based system with one place to manage the work. I’m proud that I solved the problem they actually had. I’d take that same approach when defining a data or AI solution with a Bell team.

## 6. Tell us about a time you showed initiative.

At Lux Bio, my manager initially asked me to get one pump running on a timer. While working on that, I saw how much manual work the lab team was doing around the other equipment. They had to switch between interfaces to calibrate devices, check their status, and collect readings for each production run.

I spent time with the lab team to understand those steps. Then I built a larger automation system, including device firmware, Python services, and a web interface. It brought equipment control, calibration, monitoring, and production data into one place, so the team could set up and follow a run with less manual intervention.

The system became part of their daily workflow. It helped make new protocol deployment three times faster, and weekly production doubled. That experience taught me to look at the process around an assigned task. At Bell, I’d bring that same initiative to finding and fixing a bottleneck that affects the whole workflow.

## 7. Tell us about yourself.

I’m Smarth Gupta. I graduated from UBC in May with a combined major in Computer Science and Physics. I like taking a problem that isn’t fully defined, learning from the people closest to it, and building something they can use.

At Lux Bio, I worked with the lab team to build automation and data collection software for production. More recently, I built a client management platform for a wealth management firm after interviewing and shadowing its users. I’ve also been building an AI agent platform that plans and carries out tasks across tools like email and calendars.

I’ve worked with people in research, biotech, and finance, and I’m comfortable learning a new domain from them. My physics background helps me break down unfamiliar problems and test my assumptions. I want to bring that approach to Bell’s graduate program, particularly the work in data engineering and machine learning engineering.