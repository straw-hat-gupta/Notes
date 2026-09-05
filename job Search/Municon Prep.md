
Interviewers Kelvin Filyk (Full-stack Software Developer), 

- Kelvin Filyk (Full-stack Software Developer)
	- About from LinkedIn: Full-stack software developer with an adaptable, polyglot programming mindset, excited to take on new design challenges to bring ideas to life.
- Eric Rojo (Full Stack Software Developer)
	- About from LinkedIn: has the same first line for the about section as Kelvin
- Elliott Routly (Director)
	- About from LinkedIn: Professional Expertise: Finance professional in the construction industry. Previously Infrastructure and M&A Advisory, Corporate Development (M&A, investor presentations, project development), Financial Modelling, Fundamental Valuation (project, company, and macro-economic levels), and Professional Trading and Portfolio Strategy.
## Questions:

How are you?
Bring the excitement
had a great workout this morning 

Tell me about yourself.

Current:
- I recently graduated from UBC and am working on freelance projects, most recent one being the client management platform for a wealth mangement firm in calgary. I built a platform for them to move away from the spreadsheet absed workflow they were using where 
Past
- Right before this I did contract work at a company web development company where I learnt a lot about interacting with clients and before that i worked at lux bio a biotech startup based out vancouver. 
Future
- In the future i hope to be in a role where I am able to work along more knowledgable people who i can learn from and in and solve challenging problems
Outside of work i like to cook new recipes and climb

Why this role?
**how the role connects to your experience and skills, how you’ll make an impact, and what makes you uniquely suited for it.**
Ive had experince building production systems i will make an impact by actively seeking out places i can contribute without being asked. I have experience with Working directly with operators and non-software stakeholders and Supporting systems used directly in production.


Why this company?
**Connect the company’s mission or values to something personal and professional. The more specific, the more memorable.**
a chance to work at the intersection of hardware and software. Working with real time data. Be able to work in cross functional team working with geoscientists, instrumentation technicians, managers, and external construction teams. I enjoy working in eviroments where I get to build software in close relation with stakeholders and domain experts.


What questions do you have for us?
 - What are the biggest technical challenges with the data systems platform today that you'd want the person coming into this role to help solve?
- The posting mentions that the platform has significant expansion ahead. What does that expansion look like from a product and engineering perspective?
- How is the software team structured, and how closely does the developer work with the product and field teams using the data systems systems?
- What would you want someone in this role to have accomplished after their first six months?
- How does data typically move through the system today, from an instrument in the field all the way to what a customer sees in the application?
- is the project we will be working on the Cavio application

how did you ensure you kept 

Once you moved to the implementation phase, can you describe how you translated those requirements into specific architecture or technical decisions? For instance, what considerations shaped your design of data models, API endpoints, state management on the front end, or other architectural aspects to ensure reliability and maintainability as things scaled up for their business?

- what framwork i follow
	- requirements: functional and non-functional
	- core entities and bussiness rules
	- figure out the apis/interfaces im gonna need based on the workflows i identified in the gathering requirements stage
	- then i map how the data will flow which shows me 

You might say that if security and traceability were important (given it's financial data), you designed your API endpoints to include authentication, implemented robust input validation, added detailed audit trails in your change history design at the database level. - For reliable scaling as user count increased, perhaps you broke workflows into modular services or properly indexed relevant client tables for fast queries. - On the front-end side (React), maybe state management was handled via Redux or Context to maintain one source of truth—even supporting search/filter functionality within large datasets.

I start with the functional and non-functional requirements, then identify the core domain entities and business rules, map the major workflows, determine what operations and system interfaces those workflows require, and then make the architecture decisions based on the constraints that come out of that process.

“One requirement was that clients belonged to households, referrals could come from existing clients, households could attend events, and associates could own tasks. Because those entities had strong relationships and we needed consistency across them, I chose a relational model rather than a document-oriented database.”

| Responsibility / expectation                               | Behavioral question we should prepare                                                                                                                      |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1. Build reliable production software**                  | **Tell me about a time you built a system that people depended on in a real production environment.** (lux)                                                |
| **2. Work with real-time data and interconnected systems** | **Tell me about a time you had to integrate multiple systems, services, sensors, or pieces of hardware. What made it difficult?** (lux)                    |
| **3. Solve ambiguous technical problems independently**    | **Tell me about a time you were given a problem without a clear solution and had to figure out the approach yourself.** (client platform or lux)           |
| **4. Improve or scale an existing application**            | **Tell me about a time you improved the performance, reliability, scalability, or maintainability of an existing system.** (client platform)               |
| **5. Make good software architecture/design decisions**    | **Tell me about a time you had to make an important architectural or design decision. What alternatives did you consider?** (need to get answers for this) |
| **6. Work accurately in a fast-paced environment**         | **Tell me about a time you had multiple priorities or a tight deadline. How did you make sure the work was completed correctly?**                          |
| **7. Take ownership and be self-directed**                 | **Tell me about a time you identified something that needed to be done and took ownership without being explicitly told to do it.** (lux)                  |
| **8. Communicate technical information effectively**       | **Tell me about a time you had to explain a technical problem or decision to someone with a different technical background.** (cleint or lu )              |

Questions to ask them:





Questions for Athena:

For the tell me about yourself question, I want to mention that I'm doing this, like, freelance project and stuff in my current part of it, but then also want to be like, you know, I'm a recent graduate. But do I put the recent graduate part in my past? And then also, how do I, like, they know I'm a recent graduate, right? Like, and I'm just doing this, like, freelance thing as, like, a filler in between when I get a job. So how do I say that, like, I am a recent grad from UBC, currently doing freelance work.

On my resume I put Vancouver for my location


----
# Municon West Coast company research

Current as of September 4, 2026.

## Bottom line

Municon West Coast is a small, private civil-engineering services company that turns physical conditions at construction sites into trusted, actionable data.

It designs monitoring programs, installs and maintains sensors, collects and analyzes measurements, and gives project teams near-real-time dashboards, threshold alerts, and reports. Its proprietary web application is called **Cavio**.

Municon is not primarily a sensor manufacturer or software company. Its product is an end-to-end risk-monitoring service combining field engineering, instrumentation, data infrastructure, and client-facing software. Customers hire it to prevent damage and delays, comply with project requirements, and defend against legal claims. [Municon’s company overview](https://www.municon.net/about-us)

## Company snapshot

| Category               | Details                                                                             |
| ---------------------- | ----------------------------------------------------------------------------------- |
| Founded                | 1991 as Municon Consultants                                                         |
| Current company        | Successor to Municon Consultants following a September 2018 acquisition             |
| Ownership              | Privately held; exact ownership and financials are not publicly disclosed           |
| Reported size          | 11 to 50 employees                                                                  |
| Legal entities         | Municon West Coast, Inc. in the US and Municon West Coast Monitoring Ltd. in Canada |
| Offices                | San Francisco, Pasadena, Vancouver, and Bellingham                                  |
| Primary market         | Western Canada and the western United States                                        |
| Main business          | Geotechnical and structural instrumentation and monitoring                          |
| Software product       | Cavio monitoring and notification platform                                          |
| Current developer role | Associate-level, full-time in-office Vancouver, CA$80,000 to CA$130,000             |

Its LinkedIn profile lists about 20 employees and identifies San Francisco as headquarters, although much of the management, software, and related GeoPacific activity appears connected to Vancouver. [Municon LinkedIn profile](https://www.linkedin.com/company/municon-west-coast-inc)

## Relationship with GeoPacific

Municon and GeoPacific Consultants appear to be closely affiliated and operationally integrated, likely as sister companies or under common ownership. I could not find an authoritative source explaining the exact legal structure.

Public evidence includes:

- GeoPacific says its staff provide engineering support to Municon’s US team.
    
- Several people publicly list management responsibilities at both companies.
    
- On the YVR CORE project, Municon supplied monitoring while GeoPacific supplied geotechnical engineering.
    
- GeoPacific advertises the same remote-monitoring capabilities and refers to custom software and servers.
    
- Your interview invitation being sent under GeoPacific fits this pattern.
    

GeoPacific likely supplies broader geotechnical engineering expertise, client relationships, and administrative support, while Municon specializes in instrumentation, field monitoring, and monitoring data systems. [GeoPacific’s remote-monitoring service](https://geopacific.ca/services/remote-monitoring/) and [GeoPacific’s Municon engineering-support reference](https://geopacific.ca/team/andreas-c-d-siagris/)

## What Municon sells

|Service line|What it does|Customer problem solved|
|---|---|---|
|Remote monitoring|Tracks vibration, noise, settlement, tilt, ground movement, groundwater, dust, utilities, pressure, load, and structural movement|Detects dangerous or unacceptable changes early|
|Condition surveys|Documents cracks and existing conditions using photographs, video, drones, crack gauges, 3D cameras, and lidar|Establishes evidence about whether construction caused damage|
|Geophysics|Uses MASW, seismic methods, electrical resistivity, GPR, magnetometry, and utility locating|Reduces uncertainty about underground conditions|
|Non-destructive testing|Provides concrete scanning, crosshole sonic logging, pile-integrity testing, and thermal-integrity profiling|Checks concrete and foundation quality without destructive excavation|
|Cavio platform|Presents measurements, alarms, user access, status updates, and notifications|Gives stakeholders one accessible view of monitoring data|

The company’s four formal business lines are documented on its [remote monitoring](https://www.municon.net/services/remote-monitoring), [conditions surveys](https://www.municon.net/services/conditions-surveys), [geophysics](https://www.municon.net/services/geophysics), and [non-destructive testing](https://www.municon.net/services/non-destructive-testing) pages.

### Remote monitoring instruments

Depending on the project, Municon uses equipment such as:

- Seismographs for vibration
    
- Sound-level meters
    
- Dust and air-quality monitors
    
- Piezometers and monitoring wells for groundwater
    
- Automated motorized total stations and survey prisms
    
- Tiltmeters and inclinometers
    
- Extensometers
    
- Load cells and strain gauges
    
- Crackmeters
    
- Utility-monitoring points
    
- Data loggers, modems, base stations, batteries, and solar panels
    

A vendor case study says Municon has more than 300 Sigicom INFRA units in its fleet. Municon also uses Sigicom’s INFRA Net software, illustrating that Cavio probably has to coexist with or ingest data from vendor-specific platforms. [Sigicom’s Municon case study](https://www.sigicom.com/customer-cases/a-trusted-partnership-with-sigicom/)

## How a typical engagement works

1. A contractor, developer, engineer, or asset owner identifies a construction risk.
    
2. Municon designs a site-specific monitoring plan covering instruments, locations, measurement frequency, thresholds, and reporting.
    
3. It records baseline conditions before disruptive work starts.
    
4. Technicians install and configure the instruments, communications hardware, and power systems.
    
5. Measurements travel through cellular modems, base stations, data loggers, or vendor systems to Municon’s servers.
    
6. Municon validates, processes, and analyzes the readings.
    
7. Cavio presents the information to authorized project stakeholders.
    
8. Email or SMS alerts notify selected people when configured thresholds are exceeded.
    
9. Engineers and contractors decide whether to continue work, investigate, or apply corrective measures.
    
10. Municon confirms whether the corrective action worked and produces recurring or final reports.
    

The critical distinction is that Municon does not merely provide raw sensor numbers. It provides the entire chain from field installation to decisions.

## Customers, users, and beneficiaries

|Group|What they need|Public examples|
|---|---|---|
|General contractors and construction JVs|Protect nearby infrastructure, comply with monitoring plans, avoid stoppages|EllisDon, Tutor Perini/Southland, Kiewit/Manson, American Bridge/Fluor|
|Developers|Protect projects and adjacent properties while limiting claim exposure|Bosa Properties, Onni Group|
|Infrastructure owners and agencies|Protect transportation, water, utility, and public assets|Vancouver Airport Authority, Caltrans, SFPUC, TransLink-related infrastructure|
|Engineers and consultants|Reliable measurements for design verification and project decisions|Jensen Hughes and multidisciplinary design teams|
|Property owners and neighbours|Independent evidence of movement, vibration, cracks, noise, or dust|Adjacent building owners and residents|
|Regulators and owner representatives|Proof that limits and project requirements were followed|Municipal and infrastructure stakeholders|

The buyer may be a contractor or developer, while the daily Cavio users may include project managers, geotechnical engineers, structural engineers, field technicians, owner representatives, and safety personnel.

## Problems and value delivered

|Customer problem|Municon’s value|
|---|---|
|Periodic site inspections can miss rapid changes|Automated monitoring provides frequent measurements|
|A small movement can become major structural damage|Thresholds provide earlier warning and time to intervene|
|Multiple instruments produce fragmented data|Cavio gives stakeholders one monitoring interface|
|Field access may be dangerous or expensive|Remote readings reduce unnecessary site visits|
|Contractors face allegations of property damage|Baseline and post-construction records provide neutral evidence|
|Regulators require documented compliance|Reports and historical measurements create an audit trail|
|Unknown subsurface conditions create design risk|Geophysical surveys create broader subsurface models|
|Damaging underground utilities causes injuries and delays|GPR and electromagnetic locating identify existing infrastructure|
|Conservative assumptions can increase construction cost|Measured MASW/Vs30 data can support more defensible seismic design|
|Stakeholders disagree about what happened|Independent third-party data creates a common factual record|

Customers are ultimately buying lower probability and lower impact of expensive events: structural damage, utility strikes, regulatory violations, project delays, community disputes, litigation, or safety incidents.

## Representative projects

|Project|Municon’s contribution|What it demonstrates|
|---|---|---|
|Oakland Bay Bridge|Eight contracts from 2006 to 2018 covering condition surveys, vibration, noise, underwater vibration, and custom logging|Ability to handle complex, long-running public infrastructure work|
|YVR CORE Program|Total stations, tiltmeters, vibration sensors, cellular transmission, server processing, and near-real-time web access|The complete sensor-to-software workflow|
|Gilmore Place|Multi-stage monitoring of TransLink infrastructure using tiltmeters, extensometers, prisms, inclinometers, strain gauges, and load cells|Large, multi-year, multi-instrument programs|
|SFPUC New Irvington Tunnel|Instrumentation plan, condition surveys, sound and vibration monitoring, direct SMS alarms, web presentation, and recurring reports|Monitoring around tunnelling, blasting, groundwater, and public water infrastructure|
|Super Bowl LX at Levi’s Stadium|Month-long utility locating for tents and generators in early 2026|Current operations beyond traditional building construction|

Sources: [Oakland Bay Bridge](https://www.municon.net/projects/oakland-bay-bridge), [YVR CORE Program](https://www.municon.net/projects/core-program-at-yvr-airport), [Gilmore Place](https://www.municon.net/projects/gilmore-place-phases-i-ii), [New Irvington Tunnel](https://www.municon.net/projects/sfpuc-new-irvington-tunnel), and [Super Bowl LX](https://www.municon.net/projects/superbowl-lx---levi-stadium).

## Cavio and the software platform

Municon’s June 2026 terms officially identify **Cavio** as its monitoring and notification web application.

Confirmed functionality includes:

- Sensor monitoring
    
- Alarm and operational-event handling
    
- Email and SMS notifications
    
- User notification preferences
    
- Status and system communications
    
- Encrypted storage of contact information
    
- Near-real-time data presentation
    
- Password-protected project access
    
- Automated or recurring reports
    

Municon explicitly says email and SMS notifications are supplemental and must not be the sole mechanism for emergency or safety-critical response. That means Cavio influences safety-related decisions, but the company does not represent it as a standalone emergency system. [Cavio privacy policy and terms](https://www.municon.net/sub-service/privacypolicy)

I found no evidence that Cavio is currently sold as independent SaaS. It appears to be a proprietary platform bundled with Municon’s monitoring services. The job posting’s description of it as a “growing software product with significant expansion ahead” suggests greater productization may be planned.

### Confirmed technology stack

- Node.js and Express
    
- React and Redux Toolkit
    
- TypeScript and JavaScript
    
- Microsoft Azure
    
- Azure SQL Database
    
- Azure Data Lake
    
- PM2 multiprocess applications
    
- Docker and container orchestration as desirable experience
    

[Current software-developer posting](https://ca.linkedin.com/jobs/view/software-developer-at-municon-west-coast-4459870741)

### Likely architecture

This mapping is inferred from the public stack and project descriptions:

1. Field instruments generate measurements.
    
2. Data arrives through data loggers, cellular modems, base stations, vendor APIs, or uploaded files.
    
3. Node.js workers ingest and normalize multiple instrument formats.
    
4. Processing applies unit conversions, calibration factors, validation, and threshold rules.
    
5. Azure SQL stores operational data such as organizations, projects, instruments, users, thresholds, and alarm configurations.
    
6. Azure Data Lake stores high-volume raw or historical measurement data.
    
7. Express APIs serve the web application and administrative workflows.
    
8. React and Redux Toolkit power project dashboards, charts, configuration, and user state.
    
9. Background processes generate reports and dispatch notifications.
    

Likely domain entities include clients, projects, sites, structures, instruments, sensor channels, readings, thresholds, alarms, recipients, reports, users, and roles.

### What the job-description language reveals

|Requirement|Likely reason Municon needs it|
|---|---|
|Adapter and Factory patterns|Different sensor vendors and file formats need a common interface|
|Builder pattern|Complex project, instrument, report, or alarm configurations|
|Decorator pattern|Applying validation, logging, conversions, retries, or calibration around processing|
|Facade pattern|Hiding vendor or Azure complexity behind simple domain services|
|Domain-Driven Design and Onion Architecture|Keeping monitoring rules independent of Express, Azure, and hardware vendors|
|PM2 and thread-safe coding|Preventing several processes from producing duplicate readings, alerts, or reports|
|SQL indexing and normalization|Efficiently querying large datasets while preserving consistent project configuration|
|Caching|Making historical charts and dashboards responsive|
|Redux and unidirectional flow|Keeping filters, projects, charts, selected sensors, and live updates consistent|
|Horizontal scaling|Handling more projects, instruments, readings, and concurrent users|

For Node.js, “thread safety” probably concerns process-level concurrency more than conventional shared-memory threads. Multiple PM2 workers can race through the database or a queue. Safe solutions include transactions, unique constraints, idempotency keys, atomic updates, distributed locks, and single-owner background jobs.

## Business model

Municon does not publish pricing. Its business model most likely combines:

- Monitoring-plan design and engineering fees
    
- Site mobilization and installation
    
- Instrument deployment and maintenance
    
- Ongoing data collection, hosting, analysis, and reporting
    
- One-time condition surveys, geophysical studies, and testing
    
- Longer-term monitoring contracts lasting months or years
    

This is project-based services revenue with recurring revenue during each active monitoring engagement. It is not currently a conventional subscription software business.

The reusable equipment fleet improves economics because the same instruments can serve multiple projects. The software platform also lets Municon support more instruments and clients without increasing manual reporting work at the same rate.

## Competitive landscape

Municon competes against several groups:

|Competitor type|Examples|
|---|---|
|Regional monitoring specialists|Lil Mount Monitoring, BKL|
|Large monitoring integrators|Sixense, GEO-Instruments, Geocomp|
|Broad engineering consultancies|Geosyntec, WSP, Fugro|
|Instrument and data-platform vendors|Sigicom, Terra Insights/RST Instruments, Leica|
|Internal client teams|Large contractors may buy instruments and operate monitoring themselves|

Examples of comparable offerings include [Sixense’s automated geotechnical monitoring](https://northernamerica.sixense-group.com/services/monitoring-testing/geotechnical-soil-foundations-and-retaining-structures/geotechnical-monitoring), [GEO-Instruments’ AMTS systems](https://www.geo-instruments.com/technology/amts-systems/), and [Geocomp’s monitoring services](https://www.geocomp.com/geotechnical-monitoring/).

Municon’s differentiation appears to be:

- More than 30 years of project history
    
- A specialist focus on the western US and Canada
    
- End-to-end delivery rather than hardware alone
    
- Experience on complex, high-profile infrastructure
    
- Independent third-party credibility
    
- A sizeable reusable instrument fleet
    
- Site-specific, multi-vendor monitoring programs
    
- Cavio as a unified data, alerting, and reporting layer
    
- Access to GeoPacific’s broader geotechnical expertise
    
- Several complementary services under one provider
    

Its moat is probably execution, relationships, historical experience, field expertise, and workflow integration rather than uniquely proprietary sensor technology.

## Major challenges and risks

### Technical

- Integrating many instruments, vendors, protocols, units, and sampling frequencies
    
- Handling unreliable cellular service and site power
    
- Detecting stale sensors, calibration problems, bad readings, and damaged equipment
    
- Preventing duplicate processing and duplicate alerts across PM2 workers
    
- Querying and plotting large time ranges without overwhelming Azure SQL
    
- Making alerts fast while avoiding false alarms
    
- Preserving original readings and a defensible audit history
    
- Keeping tenant and project data isolated
    
- Protecting sensitive infrastructure and project information
    
- Scaling custom reporting without creating one-off code for every customer
    

### Business

- Every construction site has unique requirements, which makes standardization difficult
    
- A missed or incorrect measurement can damage customer trust
    
- Hardware needs maintenance, calibration, replacement, and field support
    
- Larger competitors have more offices, staff, and capital
    
- Project revenue can be cyclical and dependent on construction activity
    
- Geographic growth requires local technicians, permits, equipment, and response capacity
    
- Vendor dependence creates integration and pricing risk
    
- Publicly available financial, backlog, and customer-concentration information is limited
    

The central tension is between customization and scalability. Customers value Municon because every monitoring plan is tailored to the site, but Cavio becomes easier to maintain and scale when projects follow standardized domain models and workflows.

## Current direction

Several recent signals point toward expansion:

- Cavio received formal public privacy terms in June 2026.
    
- Municon is hiring both a software developer and an estimator, suggesting investment in delivery capacity and new-project acquisition.
    
- The developer posting emphasizes horizontal scaling, containers, application health, architecture, and database performance.
    
- The company completed current work around Super Bowl LX in early 2026.
    
- It is expanding beyond basic vibration monitoring into geophysics, digital twins, utility locating, and foundation testing.
    

My interpretation is that Municon has already proven the service model and now wants to make Cavio capable of supporting more projects, sensors, offices, and customers without proportionally increasing manual work.

## What this developer role probably involves

This is unlikely to be a narrowly defined frontend or backend position. At a company this size, it probably includes:

- Building Cavio features across React, Express, and SQL
    
- Adding new sensor and vendor integrations
    
- Improving chart and historical-query performance
    
- Designing project, instrument, threshold, and alert workflows
    
- Fixing production data problems with field technicians
    
- Improving multiprocess reliability and background jobs
    
- Scaling Azure infrastructure and storage
    
- Adding application-health monitoring
    
- Supporting authentication, authorization, and project-level access
    
- Automating reports and operational tasks
    
- Gradually restructuring existing code around clearer domain boundaries
    

It is software engineering inside an engineering-services business, not a conventional software startup. You would likely work closely with geoscientists, instrumentation technicians, managers, and external construction teams.

## Your fit

This is one of the strongest domain matches between your experience and a job posting.

| Municon need                   | Your relevant experience                                      |
| ------------------------------ | ------------------------------------------------------------- |
| Physical sensor data platform  | Lux Sense SCADA and production automation                     |
| Real-time telemetry            | MQTT-based monitoring and device communication                |
| Hardware integrations          | Modbus RTU, serial devices, ESP32, ESP-NOW, Raspberry Pi      |
| Full-stack development         | React, Node.js, Express, TypeScript, Python                   |
| Data processing                | OCR pipelines, image analysis, sensor processing              |
| Operational reliability        | Supporting systems used directly in production                |
| Networking and concurrency     | TCP project and distributed-systems work                      |
| Deployment                     | Docker, Linux, homelab, production services                   |
| Cross-functional communication | Working directly with operators and non-software stakeholders |

Your strongest interview framing is:

> I have already built the same class of system in another physical domain: devices in the field, unreliable communication, backend ingestion, data processing, a dashboard, and operators making real-world decisions from the output.

Your main gaps are:

- Azure SQL and Azure Data Lake
    
- Redux Toolkit, if you have not used it directly
    
- PM2 production clustering
    
- Formal DDD, Onion Architecture, and MVVM terminology
    
- Geotechnical instrumentation concepts
    
- Safety and legal requirements around construction-monitoring evidence
    

Those are smaller gaps than the domain overlap you already have.

## Best questions to ask

1. What does “significant expansion ahead” mean for Cavio: more projects, external customers, new sensor types, or a standalone product?
    
2. What are Cavio’s largest technical bottlenecks today?
    
3. How does data reach Cavio from the different instrument vendors?
    
4. What scale does the platform currently handle in active projects, sensors, and daily readings?
    
5. How do you prevent duplicate alerts or reports when running multiple PM2 processes?
    
6. Which data belongs in Azure SQL versus Azure Data Lake?
    
7. Who sets and approves thresholds, and how does the platform preserve an audit history of changes?
    
8. How large is the software team, and how closely does it work with field technicians?
    
9. Is there an after-hours or on-call expectation when monitoring projects operate continuously?
    
10. How are Municon and GeoPacific structured, and which organization would employ and manage this role?
    
11. Are the architecture patterns in the posting already established, or is the new developer expected to help introduce them?
    
12. What would successful performance look like during the first six months?
    

## Overall assessment

Municon is an established, credible niche engineering company with real infrastructure customers and a software platform that directly supports its core service. It is not a high-growth VC software startup, but the role offers unusually direct ownership of software connected to physical systems and real-world outcomes.

For you, the main attraction is the overlap with Lux Sense and your hardware-to-dashboard experience. The main uncertainties to resolve are Cavio’s maturity, the size of the software team, how much legacy modernization is required, and whether the company has a healthy engineering process around testing, deployments, and production support.


---
### Description

_Municon West Coast is a dynamic and rapidly growing geotechnical and structural instrumentation services company that has been in business for over 30 years. We specialize in providing advanced automated monitoring systems to help ensure the safety and integrity of buildings, excavations, dams, bridges, mines, embankments, and slopes. Our cutting-edge technology and contemporary monitoring systems enable us to provide real-time data and analysis, ensuring that all parties have the information they need to manage the risk and ensure project success. We provide monitoring services on both public and private projects to contractors, engineers, and other stakeholders. With a proven track record of success and a dedication to innovation, we are committed to delivering unparalleled service to our clients._ _We exist in a fast-paced technical work environment and are a performance driven company. We take pride in providing high quality work and services to our clients and expect the same from our employees._

We are looking for a **Software Developer** to join our Vancouver-based team and contribute to the continued development of our in-house data systems platform.

This is an opportunity to work on a growing software product with significant expansion ahead. The successful candidate will be hands-on in building, improving, and scaling applications that support real-world monitoring and infrastructure projects.

This is a **full-time, in-office position based in Vancouver, BC**. We are currently considering **local candidates only**.

  

**What You'll Work With**

Our current technology stack includes:

- Node.js, Express, React, and Redux Toolkit (RTK)
- TypeScript and JavaScript
- Microsoft Azure
- Azure SQL Database
- Azure Data Lake
- Multiprocess applications using PM2
- Modern frontend state management and unidirectional data flow

**What We're Looking For**

You have strong software development fundamentals and can apply sound design and architecture principles to build reliable, scalable applications. Your experience should include:

- Object-oriented design principles, including encapsulation, abstraction, and polymorphism
- Design patterns such as Delegate, Factory/Builder, Decorator, Adapter, and Facade
- SOLID design principles
- Domain-Driven Design and Onion Architecture
- Model-View-ViewModel architecture
- Caching strategies and scalable application design
- Thread-safe coding and multiprocess applications
- Unidirectional state flow and single-source-of-truth approaches to application state
- Scalable SQL query strategies, database indexing, and database normalization
- Database tools such as DBeaver or similar platforms
- Microsoft Azure and horizontal scaling strategies

Experience with **Docker, container orchestration, and production application health monitoring** is considered an asset, particularly within an Azure environment.

  

**What You'll Bring**

- A degree in Software Engineering, Computer Science, or an equivalent field
- Relevant professional software development experience aligned with the technologies and principles above
- Strong technical problem-solving skills
- Excellent written and verbal communication skills
- The ability to work accurately and efficiently in a fast-paced environment
- Strong time management skills and the ability to meet deadlines
- A motivated, self-driven approach with a high level of ownership over your work

  

Salary: $80,000-$130,000

### Requirements

- Object-oriented design principles, including encapsulation, abstraction, and polymorphism
- Design patterns such as Delegate, Factory/Builder, Decorator, Adapter, and Facade
- SOLID design principles
- Domain-Driven Design and Onion Architecture
- Model-View-ViewModel architecture
- Caching strategies and scalable application design
- Thread-safe coding and multiprocess applications
- Unidirectional state flow and single-source-of-truth approaches to application state
- Scalable SQL query strategies, database indexing, and database normalization
- Database tools such as DBeaver or similar platforms
- Microsoft Azure and horizontal scaling strategies


