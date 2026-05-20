# Coherent Recruiter Example Workflows

This document gives recruiters copy-paste prompts for demonstrating and using the Coherent Recruiter plugin in Codex. It focuses on realistic recruiter workflows where several skills work together, not only one skill at a time.

Every output should be treated as a recruiter-owned draft. Codex can help prepare notes, messages, reports, and review aids, but the recruiter validates facts, policy, tone, and next steps before using anything.

## Start Here

- [Beginner installation guide](PLUGINS-FOR-DUMMIES.md)
- [Repository README](README.md)
- [Technical marketplace usage guide](docs/use-this-marketplace.md)
- [Coherent Recruiter plugin overview](plugins/coherent-recruiter/README.md)
- [Coherent Recruiter plugin docs](plugins/coherent-recruiter/docs/README.md)

## Human Skill Guides

Use these when you want to learn one skill at a time:

- [Candidate FAQ Responder](plugins/coherent-recruiter/docs/human-guides/candidate-faq-responder-skill.md)
- [Candidate Relevance Ranker](plugins/coherent-recruiter/docs/human-guides/candidate-relevance-ranker-skill.md)
- [CV Format Converter](plugins/coherent-recruiter/docs/human-guides/cv-format-converter-skill.md)
- [Follow-Up Finder](plugins/coherent-recruiter/docs/human-guides/follow-up-finder-skill.md)
- [JD Drafter](plugins/coherent-recruiter/docs/human-guides/jd-drafter-skill.md)
- [Job Request Gap Analyzer](plugins/coherent-recruiter/docs/human-guides/job-request-gap-analyzer-skill.md)
- [Outreach Library](plugins/coherent-recruiter/docs/human-guides/outreach-library-skill.md)
- [Pipeline Report Generator](plugins/coherent-recruiter/docs/human-guides/pipeline-report-generator-skill.md)
- [Prescreen Call Transcriber](plugins/coherent-recruiter/docs/human-guides/prescreen-call-transcriber-skill.md)
- [Recruiter Boolean Builder](plugins/coherent-recruiter/docs/human-guides/recruiter-boolean-builder-skill.md)
- [Recruiter Skill Creator](plugins/coherent-recruiter/docs/human-guides/recruiter-skill-creator-skill.md)
- [Rejection Letter Drafter](plugins/coherent-recruiter/docs/human-guides/rejection-letter-drafter-skill.md)
- [Scorecard Writer](plugins/coherent-recruiter/docs/human-guides/scorecard-writer-skill.md)

## How To Demo It

For a lecture, start with broad prompts that say `Use Coherent Recruiter`. Codex should route the request across the bundled skills. For deeper demos, ask for a specific skill by ID, such as `$jd-drafter` or `$outreach-library`.

Good demo formula:

```text
Use Coherent Recruiter to [business outcome].
Use these skills if helpful: [skill list].
Return: [specific artifacts].
Do not invent missing facts. List what I need to validate before using.

[paste role, candidate, message, transcript, table, or notes]
```

## Working With Other Codex Plugins

Coherent Recruiter can work alone from pasted text. It becomes more powerful when other Codex plugins are enabled:

- Teams: find or summarize stakeholder conversations, draft Teams updates, or prepare a message to a Delivery Manager.
- Outlook Email: search candidate threads, summarize replies, extract follow-ups, or draft candidate emails for review.
- Outlook Calendar: check availability, prepare interview scheduling options, or connect candidate communication with interview logistics.
- SharePoint: fetch shared JDs, intake templates, policies, CV templates, and pipeline documents.
- Spreadsheets: analyze CSV or Excel pipeline exports before producing a report.
- Slack: use the same patterns as Teams if the team works in Slack channels instead.

Example combined prompt:

```text
Use Outlook Email to find recent unread candidate replies about the Senior Java role, then use Coherent Recruiter to classify them into: needs FAQ answer, needs follow-up, needs scheduling, not relevant. Draft replies for recruiter review only.
```

## Example Workflow Scenarios

### 1. New Role Launch From Messy Intake

Use this to show the value of starting with gaps before writing content.

Skills used: `$job-request-gap-analyzer`, `$jd-drafter`, `$recruiter-boolean-builder`, `$outreach-library`

```text
Use Coherent Recruiter to turn this messy intake into a recruiting launch pack.
Use the smallest set of recruiter skills needed.
Return:
1. Job request gaps and clarification questions for the Delivery Manager.
2. A safe draft JD using only confirmed facts.
3. LinkedIn and Google X-ray Boolean strings.
4. One short candidate outreach draft.
5. Recruiter validation checks.

Intake:
Need senior Java developer for banking client. ASAP.
Tech: Java, Spring, maybe Kafka, cloud nice to have.
Location: Poland, hybrid maybe remote.
English good enough for client meetings.
Rate not confirmed.
Team details unknown.
Interview process probably HR plus tech.
```

### 2. Delivery Manager Clarification Message

Use this when a recruiter needs to ask better questions without sounding critical.

Skills used: `$job-request-gap-analyzer`, `$jd-drafter`

Optional companion plugin: Teams or Outlook Email

```text
Use Coherent Recruiter to analyze this job request and draft a concise Teams message to the Delivery Manager.
Limit the message to the 6 questions that block sourcing.
Keep the tone collaborative and practical.
Do not draft a full JD yet.

Job request:
Senior QA Automation. Must know Selenium, API testing, Java or JS.
Client: confidential healthcare company.
Start date: soon.
Location: EU.
Need strong communication.
```

Connected-plugin variant:

```text
Use Teams to find the latest discussion about the Senior QA Automation role, then use Coherent Recruiter to prepare a short clarification message for the Delivery Manager. Draft only; do not send.
```

### 3. Sourcing Campaign Pack

Use this to demonstrate a sourcing workflow from role brief to outreach.

Skills used: `$recruiter-boolean-builder`, `$outreach-library`, `$follow-up-finder`

```text
Use Coherent Recruiter to create a sourcing campaign pack.
Return LinkedIn Recruiter, GitHub, and Google X-ray search strings, then draft a first-touch LinkedIn message and a follow-up message.

Role:
Senior DevOps Engineer
Must-have: AWS, Terraform, Kubernetes, CI/CD, Linux
Nice-to-have: Helm, ArgoCD, observability, fintech
Location: Poland or Romania, remote EU possible
Seniority: 6+ years

Candidate example for outreach:
Anna Kowalczyk, DevOps engineer at Allegro, mentions AWS, Terraform, Kubernetes, and cost optimization in her profile.
```

### 4. Search Calibration After Bad Results

Use this when a Boolean string returns too many irrelevant profiles.

Skills used: `$recruiter-boolean-builder`, `$candidate-relevance-ranker`

```text
Use Coherent Recruiter to debug this sourcing search.
Tell me why the search is too broad, create a tighter version, and show what profile evidence I should check before contacting candidates.

Role: Senior Java Backend Engineer for fintech.
Must-have: Java 17, Spring Boot, microservices, Kafka, AWS.

Current search:
("Software Engineer" OR Developer) AND (Java OR Spring) AND cloud

Bad results I am seeing:
- Many Android Java profiles.
- Many junior developers.
- Some .NET backend profiles.
- Very few Kafka profiles.
```

### 5. Candidate Batch Review

Use this to show that the plugin suggests review order, not automated decisions.

Skills used: `$candidate-relevance-ranker`, `$cv-format-converter`

```text
Use Coherent Recruiter to review this candidate batch against the role.
Suggest the order in which I should review them.
Do not use scores, pass/fail labels, or final hiring recommendations.
For the top 2 candidates, list what would be needed before creating a client-ready profile.

Role:
Senior Java Backend. Must-have: Java 17, Spring Boot, Kafka, PostgreSQL, AWS, English B2+.

Candidates:
Candidate A: 8 years Java/Spring, Kafka in 2 projects, AWS ECS, PostgreSQL, fintech payments.
Candidate B: 10 years backend, mostly .NET, some Java maintenance, Azure, SQL Server.
Candidate C: 6 years Java, Spring Boot, PostgreSQL, no Kafka mentioned, AWS Lambda, retail.
Candidate D: 9 years Java, Kafka, microservices, GCP, English C1, recent banking project.
```

### 6. Client-Ready Profile From CV

Use this when a candidate has agreed to be presented.

Skills used: `$cv-format-converter`, `$candidate-relevance-ranker`

```text
Use Coherent Recruiter to prepare a client-ready profile draft.
First, identify missing or risky fields. Then reformat the CV.
Anonymization: FULL.
Target role: Senior Java Backend for fintech.
Preserve exact dates, technologies, metrics, and achievements. Do not make the candidate sound stronger than the CV supports.

CV:
[paste anonymized or sample CV text]
```

### 7. Prescreen Notes To Scorecard

Use this immediately after a screening call.

Skills used: `$prescreen-call-transcriber`, `$scorecard-writer`, `$candidate-faq-responder`

```text
Use Coherent Recruiter to convert these prescreen notes into recruiter-ready outputs.
Return:
1. Prescreen summary.
2. Draft scorecard.
3. Missing information to clarify.
4. Draft follow-up reply to the candidate's question, using only the supplied FAQ.

Role:
Senior Java Backend, must-have Kafka and AWS, English B2+.

Prescreen notes:
Candidate has 8 years Java, 5 years Spring Boot, used Kafka for event-driven payments platform, AWS ECS and RDS. English sounded B2/B2+. Notice period 1 month. Expected 23k-26k PLN gross. Asked whether the role is remote and whether the client allows B2B.

FAQ:
Remote setup is decided per client and must be confirmed per role. B2B availability depends on country and legal setup; recruiter must confirm before promising.
```

### 8. Candidate FAQ Response From Email

Use this when candidates ask about process, salary, remote work, contract type, or timelines.

Skills used: `$candidate-faq-responder`

Optional companion plugin: Outlook Email

```text
Use Coherent Recruiter to draft a candidate reply.
Use only the FAQ facts below. If the FAQ does not answer something, write a holding response and list what I need to confirm.

Candidate email:
"Hi, thanks for reaching out. Is this fully remote? What is the salary range? Is B2B possible? How many interview stages are there?"

FAQ:
- Remote setup depends on the client and project.
- Salary range must be confirmed by the recruiter for each role.
- B2B may be possible depending on location and legal setup.
- Standard process is recruiter screen, technical interview, and final client conversation, but some roles differ.
```

Connected-plugin variant:

```text
Use Outlook Email to fetch the latest email in this candidate thread, then use Coherent Recruiter to draft a FAQ-grounded reply. Draft only; do not send.
```

### 9. Follow-Up Cleanup From Candidate Threads

Use this for a weekly recruiter routine.

Skills used: `$follow-up-finder`, `$candidate-faq-responder`, `$outreach-library`

Optional companion plugin: Outlook Email

```text
Use Coherent Recruiter to review these candidate thread snippets and identify who needs a follow-up.
For each candidate, classify the situation as: first follow-up, scheduling nudge, FAQ answer needed, stop following up, or recruiter decision needed.
Draft short messages for recruiter review.

Threads:
1. Marek: first outreach sent 8 days ago, no reply.
2. Anna: asked whether the DevOps role is remote, no answer sent yet.
3. Pavel: agreed to interview but did not confirm the proposed time.
4. Julia: two unanswered follow-ups after initial outreach.
```

Connected-plugin variant:

```text
Use Outlook Email to search candidate messages from the last 10 days that likely need follow-up, then use Coherent Recruiter to group them and draft follow-up messages for review.
```

### 10. Interview Scheduling Support

Use this to demonstrate how recruiting content connects to calendar work.

Skills used: `$candidate-faq-responder`, `$follow-up-finder`

Optional companion plugin: Outlook Calendar

```text
Use Coherent Recruiter to draft an interview scheduling message to the candidate.
Keep it warm and brief.
Include these available slots and ask for confirmation.
Do not promise anything beyond the slots listed.

Candidate: Maria
Role: Senior Java Backend
Slots:
- Tuesday 10:00-10:45 Warsaw time
- Wednesday 14:00-14:45 Warsaw time
- Thursday 11:30-12:15 Warsaw time
Interview: technical interview with engineering team
```

Connected-plugin variant:

```text
Use Outlook Calendar to find three open 45-minute slots this week, then use Coherent Recruiter to draft a candidate scheduling email. Draft only; do not send.
```

### 11. Interview Feedback To Rejection Message

Use this to show safe candidate communication after feedback.

Skills used: `$scorecard-writer`, `$rejection-letter-drafter`

```text
Use Coherent Recruiter to turn this interviewer feedback into a draft scorecard and a stage-3 rejection email.
First flag any conflicting or risky feedback. Then draft the candidate-facing message using only safe, role-related feedback.

Role: Senior Frontend Engineer, React/Next.js required.
Feedback:
Interviewer 1: Strong Vue/Nuxt background, clear communication, but limited production React and no Next.js examples.
Interviewer 2: Good general frontend knowledge, weaker on performance optimization in React.
Recruiter note: Candidate invested time and was positive throughout the process.
```

### 12. Candidate Update After Positive Interview

Use this to avoid leaking unapproved feedback while keeping the candidate warm.

Skills used: `$scorecard-writer`, `$candidate-faq-responder`, `$follow-up-finder`

```text
Use Coherent Recruiter to draft a candidate update after interview.
Use the interviewer notes to create an internal recruiter summary first.
Then write a short candidate-facing update that does not reveal confidential feedback or final decisions.

Interviewer notes:
Strong backend fundamentals, good Kafka examples, AWS experience relevant. Need client confirmation on budget and project start date. Next step likely client conversation, not confirmed yet.

Candidate question:
"Do you already know if I passed the technical interview?"
```

### 13. Weekly Pipeline Report

Use this for a management-facing demo.

Skills used: `$pipeline-report-generator`, `$follow-up-finder`, `$job-request-gap-analyzer`

Optional companion plugin: Spreadsheets, Teams, or Outlook Email

```text
Use Coherent Recruiter to create a weekly pipeline report for a Delivery Manager.
Do not invent metrics. If a number is missing, say it is missing.
Return: summary, bottlenecks, data quality issues, recommended recruiter actions, and a short Teams update.

Pipeline data:
Role | New CVs | Screened | Tech Interview | Offer | Rejected | Stale > 7 days
Senior Java | 18 | 7 | 3 | 0 | 5 | 4
DevOps AWS | 11 | 4 | 2 | 1 | 2 | 1
QA Automation | 7 | 2 | 0 | 0 | 3 | 5

Notes:
QA role still lacks confirmed remote policy and salary range.
Senior Java has several candidates waiting for interview feedback.
```

Connected-plugin variant:

```text
Use Spreadsheets to inspect this pipeline export, then use Coherent Recruiter to write a Delivery Manager update. If Teams is available, draft a Teams post for review.
```

### 14. Intake Quality Trend Report

Use this to show how repeated intake problems can become process improvements.

Skills used: `$pipeline-report-generator`, `$job-request-gap-analyzer`

```text
Use Coherent Recruiter to analyze these job request issues across roles.
Return a pattern summary, top recurring missing fields, impact on sourcing, and a polite recommendation for Delivery Managers.

Recent JR issues:
1. Senior Java: missing salary range, remote policy unclear, interview process unknown.
2. QA Automation: must-have programming language unclear, client domain confidential, start date vague.
3. DevOps: cloud provider changed from AWS to Azure after sourcing started.
4. Business Analyst: English level and stakeholder location not specified.
5. Project Manager: seniority says senior, years of experience says 2+.
```

### 15. Hiring Manager Calibration Pack

Use this before a calibration meeting.

Skills used: `$jd-drafter`, `$candidate-relevance-ranker`, `$recruiter-boolean-builder`

Optional companion plugin: Teams or Outlook Calendar

```text
Use Coherent Recruiter to prepare a calibration pack for a hiring manager meeting.
Return:
1. Role requirements that are clear.
2. Requirements that need calibration.
3. Candidate evidence patterns from the sample profiles.
4. Suggested Boolean changes.
5. Questions to ask in the meeting.

Role brief:
Senior Java Backend, fintech, Kafka, AWS, PostgreSQL, microservices, English B2+.

Sample profiles:
A: Java/Spring/AWS, no Kafka visible.
B: Java/Kafka/GCP, strong banking, no AWS.
C: Java/Spring/Kafka/AWS, mostly e-commerce not fintech.
D: Kotlin backend, Kafka, AWS, no Java recent.
```

Connected-plugin variant:

```text
Use Outlook Calendar to find my next meeting with the hiring manager for Senior Java, then use Coherent Recruiter to prepare a calibration brief from these notes.
```

### 16. Re-Engagement Campaign For Talent Pool

Use this for stale candidates or silver-medalist candidates.

Skills used: `$outreach-library`, `$follow-up-finder`, `$candidate-faq-responder`

```text
Use Coherent Recruiter to create a re-engagement campaign.
Return one email and one LinkedIn version.
Keep it specific, human, and low-pressure.

Role now:
Senior DevOps Engineer, AWS, Terraform, Kubernetes, remote EU.

Candidates:
1. Anna: spoke last year, said "ping me in spring", strong AWS/Terraform.
2. Tomasz: rejected offer due to onsite requirement, current role supports remote EU.
3. Elena: no reply after first message 9 months ago, profile now mentions Kubernetes platform work.

Do not invent personal details beyond what is listed.
```

### 17. Multilingual Candidate Communication

Use this when recruiters work across markets.

Skills used: `$outreach-library`, `$candidate-faq-responder`, `$rejection-letter-drafter`

```text
Use Coherent Recruiter to draft candidate communication in Polish and English.
Create:
1. A Polish LinkedIn first-touch message.
2. An English follow-up.
3. A short Polish answer to the candidate's B2B question using only the supplied FAQ.

Role:
Senior Java Backend, Warsaw or remote Poland, fintech project.

Candidate:
Marek, Java/Spring engineer, banking and Kafka experience.

FAQ:
B2B depends on the candidate's location and legal setup. The recruiter must confirm before promising it.
```

### 18. Candidate Submission Package

Use this when preparing a candidate for client review.

Skills used: `$cv-format-converter`, `$scorecard-writer`, `$candidate-faq-responder`

Optional companion plugin: SharePoint or Outlook Email

```text
Use Coherent Recruiter to prepare a candidate submission package.
Return:
1. Client-ready profile draft.
2. Recruiter summary.
3. Missing fields to confirm with the candidate.
4. Draft candidate email asking for missing details.

Target role:
Senior Java Backend, Kafka, AWS, fintech.

Candidate CV:
[paste CV]

Recruiter notes:
Candidate confirmed interest. Notice period may be 4 weeks, not fully confirmed. Salary expectation missing. English likely B2, needs validation.
```

Connected-plugin variant:

```text
Use SharePoint to fetch the client CV template, then use Coherent Recruiter to format this candidate profile against that template. Draft only; do not upload or send.
```

### 19. Candidate Question After Rejection

Use this to demonstrate tone and policy guardrails.

Skills used: `$rejection-letter-drafter`, `$candidate-faq-responder`, `$scorecard-writer`

```text
Use Coherent Recruiter to draft a reply to this candidate after rejection.
Use only safe, role-related feedback. Do not mention interviewer names. Do not include protected characteristics or subjective culture-fit language.

Candidate message:
"Thanks for the update. Can you tell me why I was rejected? I thought the interview went well."

Approved feedback:
The role needed deeper production React and Next.js experience. Candidate's strongest recent examples were Vue/Nuxt. Communication was positive.

Stage:
Technical interview completed.
```

### 20. Build A New Recruiter Skill From A Course Idea

Use this to show that the marketplace can grow over time.

Skills used: `$recruiter-skill-creator`

```text
Use Coherent Recruiter and $recruiter-skill-creator to turn this course idea into a new Codex skill package plan.
Return: proposed skill name, SKILL.md outline, human guide outline, eval checklist ideas, and connections to existing Coherent Recruiter skills.

Course idea:
Recruiters need a reusable workflow for preparing hiring-manager calibration meetings. It should combine role intake notes, sample candidate profiles, market feedback, and questions for the stakeholder.
```

## Fast Lecture Demo Sequence

If you only have 20-30 minutes, use this order:

1. Scenario 1: show end-to-end role launch from a messy intake.
2. Scenario 3: show Boolean and outreach generation.
3. Scenario 5: show candidate review order without scores.
4. Scenario 7: show prescreen notes to scorecard.
5. Scenario 13: show pipeline report and Teams-style update.

This sequence demonstrates intake, sourcing, communication, candidate review, interview documentation, and reporting.

## Safety Reminders For Recruiters

- Do not paste confidential client or candidate data unless your internal policy allows it.
- Do not send generated messages without reviewing them.
- Do not treat suggested review order as a hiring decision.
- Do not ask Codex to invent salary, remote policy, visa policy, timeline, or client details.
- Do not share interview feedback with candidates unless it is approved and safe to share.
- Do use Codex to list missing facts and validation checks.

## Pattern Library

Use these mini prompts to adapt any scenario:

```text
Use Coherent Recruiter. Ask only for blocking missing inputs before drafting.
```

```text
Use Coherent Recruiter. Give me the recruiter validation checklist before the final draft.
```

```text
Use Coherent Recruiter. Draft only; do not imply anything was sent or decided.
```

```text
Use Coherent Recruiter. Use only the facts below and flag anything that needs confirmation.
```

```text
Use Coherent Recruiter. Make this suitable for a non-technical Delivery Manager.
```
