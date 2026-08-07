
You should run this as a structured discovery interview, not as a request for the stakeholder to design the application. Your goal is to understand the business, current workflows, problems, rules, exceptions, and priorities.

Do not try to ask every question in one meeting. I recommend three sessions:

1. Product vision and priorities
    
2. Current workflows and user journeys
    
3. Business rules, permissions, data, and exceptions
    
			
Record the meeting if the stakeholder agrees. Do not put real client names, account numbers, financial details, or other confidential information into Claude or Codex afterward. Replace them with synthetic examples.

# Session 1: Product vision and priorities

These answers will primarily populate `vision.md`.

## A. Why the platform is being built

### 1. Can you describe why you decided to build this platform?
to simplyfy my office life. there are so many different parts that we are maintaining separatly. get rid of redundant jobs
What you are trying to learn:

- What triggered the project
    
- Why the current approach is no longer sufficient
		the spreadsheets used to maintained the workflows are maintained separatly. 
    
- Whether the primary motivation is efficiency, risk reduction, growth, reporting, client service, or something else
    efficient and smoothness.

Useful follow-ups:

- Was there a particular event or recurring problem that led to this decision?
    the reoccuring problem is they are not able to update and sometimes they are missed.
- Why does the firm need this now?
    needed it before as well. 
- What happens if the firm continues using its current process?
    

### 2. What are the three biggest problems with the current way of working?

Ask the stakeholder to rank them.

Possible examples, without suggesting that these are necessarily true:

- Finding current client information
    
- Duplicate information--
    
- Manual data entry-- 
    
    
- Tracking workflow status
    
- Knowing who is responsible for the next action
    
- Following up on overdue tasks
    
- Correcting spreadsheet errors

    

Follow up on each problem:

- How often does this happen?
    
- Who is affected?
    
- How much time does it consume?
    
- What is the consequence when it goes wrong?
    
- How is it handled today?
    

### 3. In one sentence, what should this platform allow the firm to do that it cannot do reliably today?

This helps create the one-sentence product vision.

If the answer becomes a feature list, redirect with:

> What business outcome would those features produce?

### 4. What would make you consider this project a failure?

This often reveals critical expectations that do not appear in feature discussions.
if we are not able to produce the reports we want. 
Possible follow-ups:

- What outcomes would be unacceptable?
    
- What would cause employees not to use it? too time consuming and not intuitive. 
    
- What could cause the firm to stop using it?
    
- What types of mistakes would be especially serious?
    

## B. Users and stakeholders

### 5. Who will use the platform regularly?

For each type of user, determine: consutants and the assistant angela

- Their job or role
    
- What they are responsible for
    
- How frequently they would use the platform
    
- What information they need
    
- What actions they need to perform
    
- What they should not be allowed to do
    

Do not assume that formal job titles map directly to system roles.

### 6. Who may not use the platform directly but is affected by it?

Examples might include:

- Clients

This distinguishes direct users from affected stakeholders.

### 7. Who has final authority over product decisions?

Clarify whether different people own different kinds of decisions:

- Product priorities
    
- Business workflows
    
- Client data
    
- Security and permissions
    
- Compliance requirements
    
- Final acceptance of a release
    

Ask:

> If two stakeholders disagree about a requirement, who makes the final decision?

### 8. Who will administer the platform?

Determine who will handle:

- Creating and disabling users
    
- Assigning roles
    
- Correcting data
    
- Managing reference values
    
- Reviewing failed imports
    
- Responding to operational problems
    

## C. Desired outcomes

### 9. What should become faster or easier after the platform is introduced?

For each answer, ask:

- How is it done today?
    
- Approximately how long does it take?
    
- How often is it performed?
    
- What would a meaningful improvement look like?
    

This gives you possible success measures.

### 10. What should become safer or more reliable?

You are looking for outcomes such as:

- Fewer duplicate records
    
- Fewer missed follow-ups
    
- More reliable reporting
    
- Clear ownership
    
- Better permission enforcement
    
- More complete history
    
- Safer imports and corrections
    

Ask for concrete examples of current risks.

### 11. What decisions should the platform help employees make?
lots, all the tasks the system is creating that the team is missing. tasks should not be missed. 

Clarify whether the platform should:

- Present information
    
- Calculate or summarize information yes
    
- Recommend an action: yes
    
- Automatically take an action: no
-
These are very different levels of responsibility.

For each decision, ask:

- Who is responsible for the final decision?
    
- What information do they need?
    
- Must the reasoning or evidence be recorded?
    
- Can the system act automatically, or must a person approve it?
    

### 12. How should the platform improve the client experience, even if clients never use it directly?

Possible outcomes include:

- Faster responses: yes 
    
- Fewer repeated information requests: not really as this platform is more internal. 
    
- Better follow-ups: very important
    
- Smoother onboarding: yes
    
- Fewer errors: yes
    
- More consistent communication: yes
    

## D. Scope and priorities

### 13. Which workflows must the first useful version support?

Ask the stakeholder to rank the workflows instead of declaring all of them essential.

Possible candidates:

- Referrals: most impartant 1
becase this is the core of the bussiness as this is what gives more money
- Prospective clients 5
    
- Client onboarding 4
    
- Client and household information
    
- Investment opportunities 3
    
- Transfers: 2
    
- Relationship-management tasks 6
    
- Spreadsheet imports
    
- Search: 1
    
- Reports: 1
    
- Audit history 7
    
- User and permission management
    

Ask:

> If the first release could support only three workflows, which three would you choose and why?

### 14. What does the first version explicitly not need to do?

This protects the project from uncontrolled scope growth.
investment transfer
Ask about possible exclusions such as:

- Trading
    
- Portfolio accounting
    
- Custody
    
- Financial planning calculations
    
- Client portal
    
- Automated investment recommendations
    
- Email automation
    
- Mobile application
    
- Advanced analytics
    
- AI features
    
- Replacement of every existing spreadsheet
    

Do not suggest that these must be excluded. Ask the stakeholder to decide.

### 15. Which existing systems will remain in use?

For each system or spreadsheet, ask:

- What is it used for?
    
- Who maintains it?
    
- Is it considered authoritative?
    
- Will the new platform replace it or integrate with it?
    
- How frequently does its data change?
    
- Can data be exported?
    
- Are there restrictions on integration?
    

### 16. What should the platform never attempt to replace?

This establishes durable product boundaries.

## E. Success measures

### 17. How will we know the first release is useful?

Ask for observable evidence, such as:

- Employees use it for a particular workflow
    
- A specific spreadsheet is no longer required
    
- Reports take less time to prepare
    
- Fewer records require manual correction
    
- Fewer follow-ups are missed
    
- Users can retrieve information faster
    

### 18. What should we measure before development begins?

Possible baseline measurements:

- Time required to prepare a report
    
- Time required to find a client record
    
- Number of spreadsheets involved in onboarding
    
- Number of duplicate records
    
- Number of missed or overdue tasks
    
- Time required to reconcile an import
    
- Number of manual handoffs
    

### 19. What would success look like three months after launch?

Then ask the same question for twelve months after launch. This separates immediate adoption from longer-term value.
be able to provide value to the clients. more prompt to get to clients more consistant. les s time managing the workflow more time spent interacting with clients. 
### 20. Who is responsible for evaluating whether the product is successful?

# Session 2: Current workflows and journeys

These answers will populate `journeys.md`.

For every important workflow, repeat the following questions. Start with referral management, prospect management, onboarding, and spreadsheet imports.

## A. Establish the journey

### 21. Please walk me through how this process works today, from beginning to end.

Tell the stakeholder:

> Please describe what actually happens today, including spreadsheets, emails, phone calls, and manual work. We can discuss the ideal process afterward.

As they explain, capture:

- Starting event
    getting and intro, then we use rms to put their details, book the first meeting, new referral is part of the pillar list, identifu potential bussiness, discuss nccp and all those meetings, once confirmed we add them to investment transfer. rms stops when ref becomes cleint, pillar list is for new bussiness either from new old clients. 
- People involved
    rms is managented by by 1 pillar list is managed by 2 people, reports are needed. 
- Documents or systems used
    
- Sequence of actions
    
- Decisions
    
- Handoffs: 
    
- Final outcome
    

### 22. What triggers this process?

A trigger is the event that causes someone to begin the workflow.

Examples:

- A referral is received<-
    
- A prospect agrees to proceed
    
- Transfer paperwork arrives
    
- A spreadsheet is received
    
- A client requests a change
    
- A task reaches its due date
    

Ask whether the trigger can arrive through multiple channels.

### 23. Who starts the process, and who is responsible for completing it?

Starting a workflow and owning its final outcome may belong to different people.
anyone in the firm
Ask:

- Can ownership change?
    
- Who is responsible when no one is assigned?
    
- Can multiple people own it?
    
- Who can reassign it?
    

### 24. What information must be available before the process can begin?

Separate information into:

- Required to start, refferals name phone email
    
- Required before completion
    assets, 
- Helpful but optional
    
- Unknown at the beginning
    

This prevents the system from requiring too much information too early.

### 25. What is the successful end state?

Ask what evidence proves completion.

Examples:

- An onboarding stage is approved
    
- Required documents are received
    
- A transfer is completed
    
- Imported records are reconciled
    
- A referral receives a final disposition
    
- A task is completed and recorded
    

## B. Understand every step

### 26. What is the first action the employee takes?

Then repeat:
entering info in the rms
- What happens next?
    
- Who performs that action?
    
- What information do they need?
    
- Where do they get that information?
    
- What do they produce?
    
- Who receives it next?
    

Continue until the journey is complete.

### 27. At which points does someone make a decision?

For every decision, ask:

- Who makes it?
    
- What options do they have?
    
- What information do they consider?
    
- Is approval required?
    
- Must they explain their decision?
    
- Can the decision be changed later?
    
- Should the previous decision remain visible?
    

### 28. Where does work pass from one person to another?

For every handoff, ask:

- How does the next person know work is waiting?
    
- What information accompanies it?
    
- What happens if the recipient is unavailable?
    
- Who remains accountable?
    
- Is there a deadline?
    

### 29. Which steps happen outside the system?

Examples include:

- Phone calls: recorded in rms, when date, 
    
- Emails: not recorded, 
    
- Meetings: recorded, 
    
- Document signing: date of document signed. 
    
- Work in another application
    
- External professional review
    no

The platform may need to record that an external action occurred without performing it.

### 30. How do employees know what needs attention next?

Ask whether they currently rely on:
going through all the spreadsheets. 
- Memory
    put stuff from the spreadsheets into sales force or copying stuff into the calendar from the spreadsheets.  
    

Then ask what they would prefer to see in the platform. 
reminders / alerts / emails

## C. Statuses and state changes

### 31. What statuses can this item move through?
terminilogy not in place but would be good to have terminology. 
For example, a prospect might be:

-
    

### 32. Are the status definitions currently consistent across employees?

If not, capture each interpretation and mark the final definition as `TBD`.
no further action required, apna (advneced prep for n), bna book next appointemetn, 
### 33. Which changes should happen automatically, and which require confirmation?

Ask what should occur when:

- Required information is completed: 
    
- A deadline passes: yes be informed, 
    
- An import finishes
    
- Approval is granted
    
- A related record changes
    
- An external event is recorded
    

## D. Exceptions and failures

### 34. What are the most common exceptions to the normal process?

Encourage the stakeholder to describe inconvenient real cases.

Examples:

- Missing information: 
    
- Duplicate client: might happen 
    
- Incorrect spreadsheet: no
    
- Client changes their mind: all the time. 
    
- Transfer is rejected: happens 
    
- Owner is unavailable
    
- A task is assigned incorrectly: sometimes need to change who the task is assigned to. 
    
- Information conflicts between systems: could be possible. 
    
- A process needs to be reopened
    

### 35. What mistakes do employees commonly make?
wrong amount, not doing task assigned, not updating, input errors 

For each mistake, ask:

- How is it detected?
    from manual review,
- What damage can it cause?
    dont follow up lose client, dont follow uup refs
- Who can correct it?
    
- Should correction require approval?
    no
- Should the original value remain visible?
    
- Should anyone be notified?
    

### 36. What happens when the process fails halfway through?

You need to understand whether the system should:

- Preserve completed steps
    preserve
- Roll back the entire operation
    
- Allow safe retry
    
- Create a review task
    
- Notify an administrator
    
- Prevent duplicate processing
    

### 37. Can completed work be reopened or reversed?
yes it can be reopened
Ask:

- Who can do it?
    
- When is it allowed?
    
- Is a reason required?
    
- Should an approval be required?
    
- What history must be preserved?
    

### 38. What happens when two employees update the same information?

The stakeholder may not know the technical answer. You are learning the desired business behaviour:

- Last update wins
    
- Warn the second employee
    
- Require manual reconciliation
    
- Lock the record temporarily
    
- Preserve both submissions for review
    

Mark it `TBD` if they are unsure.

## E. Time, reminders, and escalation

### 39. Does this journey have deadlines or expected completion times?

For each deadline, ask:

- When does the timer start?
    
- Are weekends or holidays included?
    
- Is it a legal, contractual, internal, or preferred deadline?
    
- Who owns the deadline?
    
- What happens when it is missed?
    

Do not encode an approximate policy as a confirmed rule.

### 40. Which events should generate reminders?

Ask:

- Who should receive the reminder?
    
- How far in advance?
    
- Through which channel?
    
- Should reminders repeat?
    
- When should they stop?
    
- Can a user dismiss or defer one?
    

### 41. When should overdue work be escalated?

Determine:

- Who receives the escalation
    
- Whether the original owner remains responsible
    
- Whether escalation changes the status
    
- Whether the escalation must be recorded
    

# Session 3: Data, permissions, audit, and business rules

## A. Core business concepts

### 42. What are the main types of records the firm works with?

Ask the stakeholder to define terms such as:

- Person
    
- Client
    
- Prospective client
    
- Household
    
- Account
    
- Referral
    
- Opportunity
    
- Transfer
    
- Task
    
- Advisor or portfolio manager
    
- External professional
    

For every term, ask:

- What makes it distinct?
    
- Can it exist independently?
    
- How is it related to other records?
    
- Can its type change?
    
- What examples are commonly confused?
    

These definitions should eventually go into your glossary, likely `CONTEXT.md`, rather than `vision.md`.

### 43. How do you determine whether two records refer to the same person or entity?

Ask:

- Which fields are compared?
    
- How reliable are those fields?
    
- Who decides whether records are duplicates?
    
- Can records be merged?
    
- Can a merge be reversed?
    
- What history must remain?
    

### 44. Which information changes frequently, and which information should be treated as historical?

This helps distinguish editable current values from records that require version history.

### 45. Which system or document is authoritative for each kind of information?

Ask this separately for:

- Identity and contact information
    
- Client status
    
- Account information
    
- Assigned advisor
    
- Transfer status
    
- Compliance information
    
- Documents
    
- Workflow status
    

There may not be one universal source of truth.

## B. Spreadsheet imports

### 46. Which spreadsheets will the platform need to import?

For each spreadsheet, ask:

- Who creates it?
    
- Where does it come from?
    
- How frequently is it received?
    
- Is its format consistent?
    
- Approximately how many rows does it contain?
    
- Does it contain multiple sheets?
    
- Which columns are required?
    
- Are column names stable?
    
- Does it contain sensitive information?
    
- Can you obtain sanitized sample files?
    

### 47. What should happen before imported data changes the platform?

Ask whether users need:

- File-format validation
    
- Column mapping
    
- A preview
    
- Duplicate detection
    
- Row-level warnings
    
- Row-level rejection
    
- Summary totals
    
- Explicit confirmation
    

### 48. If some rows are invalid, should valid rows still be imported?

Possible choices include:

- Reject the entire file
    
- Import valid rows and reject invalid rows
    
- Allow the employee to choose
    
- Require an administrator to approve partial imports
    

The stakeholder must choose based on operational needs.

### 49. What should happen if the same file is uploaded twice?

Ask whether the system should:

- Reject it
    
- Detect that it was previously processed
    
- Preview the potential duplicate effect
    
- Permit reprocessing after confirmation
    
- Safely update existing records
    

### 50. How should users correct import errors?

Determine whether they should:

- Correct the original spreadsheet and upload again
    
- Correct rows inside the platform
    
- Download an error report
    
- Ask an administrator to resolve them
    

### 51. What evidence must remain after an import?

Potential evidence includes:

- Original filename
    
- File checksum
    
- Upload time
    
- User
    
- Row counts
    
- Accepted rows
    
- Rejected rows
    
- Error reasons
    
- Resulting record changes
    

Ask what is operationally or legally necessary.

## C. Permissions

### 52. What actions can each type of user perform?

Work through actions, not only screens:

- View
    
- Create
    
- Edit
    
- Assign
    
- Approve
    
- Reject
    
- Delete
    
- Export
    
- Import
    
- Merge
    
- Reopen
    
- View history
    
- Manage users
    

### 53. Is access based only on role, or also on relationships to the record?

For example:

- All portfolio managers can see all clients
    
- A portfolio manager sees only assigned clients
    
- A team sees records assigned to its members
    
- Administrators see everything
    
- Sensitive fields have separate restrictions
    

### 54. Are there fields that some users may know exist but may not view?

This distinguishes:

- Hidden records
    
- Hidden fields
    
- Read-only fields
    
- Masked values
    
- Restricted actions
    

### 55. Who can export data?

Ask:

- Which data may be exported?
    
- In what format?
    
- Is approval required?
    
- Should exports be logged?
    
- Should exports be limited or watermarked?
    
- Can users export only records they can already view?
    

### 56. Who can delete records?

Also ask whether the stakeholder actually means:

- Hide
    
- Archive
    
- Deactivate
    
- Mark as entered in error
    
- Permanently delete
    

For financial operations, permanent deletion may be inappropriate, but the applicable policy must be confirmed.

## D. Audit and corrections

### 57. Which actions must be recorded in the audit history?

Consider asking about:

- Record creation
    
- Field changes
    
- Status changes
    
- Ownership changes
    
- Approvals
    
- Rejections
    
- Imports
    
- Exports
    
- Permission changes
    
- Merges
    
- Archiving
    
- Failed access attempts
    

### 58. What must an audit entry show?

Potential fields include:

- Actor
    
- Time
    
- Action
    
- Previous value
    
- New value
    
- Reason
    
- Related record
    
- Source, such as manual edit or import
    

### 59. Who may view audit history?

Ask whether access differs between:

- Regular employees
    
- Managers
    
- Administrators
    
- Compliance reviewers
    
- External auditors
    

### 60. How should an incorrect historical entry be handled?

Ask whether users should:

- Correct the current record while preserving history
    
- Add a correction entry
    
- Request administrator approval
    
- Never modify the original event
    

## E. Documents and sensitive information

### 61. What kinds of documents will the platform store or reference?

For each document type, ask:

- Who uploads it?
    
- Who can view it?
    
- Can it be replaced?
    
- Should old versions remain available?
    
- Does it expire?
    
- Does it require approval?
    
- Must download activity be logged?
    
- Is the platform storing the file or only a link?
    

### 62. Which information is especially sensitive?

Ask about categories, not actual client examples:

- Contact information
    
- Identification information
    
- Financial holdings
    
- Account numbers
    
- Tax information
    
- Suitability information
    
- Relationship notes
    
- Documents
    
- Credentials
    

### 63. Are there rules about how long information must be retained?

Record the stakeholder’s understanding, but mark it as requiring professional confirmation if necessary.

Ask:

- What must be retained?
    
- For how long?
    
- Who can authorize removal?
    
- Are backups included?
    
- What happens when a client relationship ends?
    

# Closing questions for every interview

### 64. Which parts of what we discussed are confirmed policy?

### 65. Which answers are based on current habits rather than formal rules?

### 66. Which questions require someone else’s approval?

Get the person’s name or role and the decision they own.

### 67. What assumptions have I made that are incorrect?

This is one of the most useful questions in the interview.

### 68. What important case have I not asked about?

### 69. Can you show me a sanitized example of how this is handled today?

Use sanitized or synthetic examples only. Useful materials might include:

- Blank spreadsheet templates
    
- Redacted forms
    
- Status lists
    
- Report layouts
    
- Process diagrams
    
- Standard operating procedures
    
- Example email templates without client information
    

### 70. What should we discuss in the next meeting?

# How to take notes

For every important statement, classify it:

```md
- Confirmed: The stakeholder has authority and explicitly confirmed it.
- Assumption: This appears true but needs validation.
- TBD: A decision has not been made.
- Professional review required: Legal, privacy, compliance, tax, or
  financial interpretation must be reviewed appropriately.
```

Use this note format:

```md
## Topic: Referral ownership

- Statement: Every new referral must have a responsible employee.
- Classification: Confirmed
- Decision owner: [Role or name]
- Source: Stakeholder interview on [date]
- Follow-up: Determine what happens when the employee is unavailable.
```

# Suggested first interview agenda

For a 60-minute first meeting:

- 5 minutes: Explain the purpose of the interview
    
- 15 minutes: Problems and reasons for the product
    
- 10 minutes: Users and decision makers
    
- 15 minutes: First-release scope and priorities
    
- 10 minutes: Success measures and risks
    
- 5 minutes: Review open questions and schedule the workflow session
    

You can open with:

> I want to understand the business problems, desired outcomes, and boundaries of the platform before we discuss detailed features. I will ask about how work is performed today and what needs to improve. If an answer is uncertain, I will record it as an open question rather than treating it as a requirement.

After the interview, first organize the notes into `vision.md`. Do not create OpenSpec requirements until the stakeholder has reviewed and corrected the vision.