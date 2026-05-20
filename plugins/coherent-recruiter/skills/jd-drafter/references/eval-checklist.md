# JD Drafter Eval Checklist

Use this reference only when validating or revising the skill. Do not load it for normal JD drafting unless the user asks to evaluate the skill.

## Smoke Tests

Run these prompts in fresh chats:

```text
Hiring manager intake notes:
Role: Senior Backend Engineer
Project: e-commerce platform for a Polish retail client, anonymize as "Top-3 Polish retailer"
Tech: Java 17, Spring Boot 3, PostgreSQL, AWS ECS/RDS/SQS, Kafka
Team: 8 engineers, 1 PM, 1 architect
Location: Warsaw or remote within Poland
Hybrid: 2x/week office for senior+
English: B2+
Years: 6+ years backend, 3+ years Spring
Domain: e-commerce or fintech preferred
Start: ASAP, ideally within 4 weeks
Comp: not disclosed in JD; competitive based on experience
Process: HR screen, tech interview, system design, final with hiring manager
```

```text
Need a senior Java dev for a banking client. ASAP.
```

```text
Senior Engineer role, 10+ years required.
We need someone Mid-Senior, 3-5 years.
Tech stack: Java OR .NET.
Location: must be in Warsaw, but fully remote is also fine.
Salary: junior range, around 8-10k PLN.
```

```text
Senior Recruiter for our internal People team.
Must-haves: 7+ years agency or in-house, IT staffing experience, fluent EN+RU, Lithuania-based or remote Baltics.
Reports to Head of TA.
```

## Regression Checks

### Complete Intake

Input:

```text
Role: Senior Frontend Engineer
Client: anonymized as "European insurance carrier"
Project duration: 12-month engagement, possible extension
Start: within 3-4 weeks
Tech: React 18, TypeScript, Next.js, Tailwind, REST + GraphQL clients
Team: 6 frontend engineers, distributed across PL/RO/UA
Location: remote within EU; quarterly Warsaw or Bucharest visits
English: C1 required
Years: 6+ years frontend, 3+ years React, 1+ year Next.js
Nice-to-have: GraphQL Apollo, design systems, WCAG 2.1
Comp: not disclosed in JD
Process: HR screen, live coding, design discussion, client final
```

Expected:
- Gap analysis marks most fields clear.
- Any missing fields are specific, such as reporting line or official boilerplate.
- Draft mirrors React 18, TypeScript, Next.js, Tailwind, REST and GraphQL.
- Does not invent salary, client name, framework versions, reporting line, or team details.
- Includes all required JD sections or marks missing official boilerplate.
- Ends with recruiter and hiring-manager validation marker.

### Sparse Input

Input:

```text
Need a senior Java developer for a banking client. ASAP.
```

Expected:
- Gap analysis marks most fields missing.
- Each missing field has a specific clarification question.
- Flags `ASAP` as needing a concrete timeline.
- Does not produce a polished JD full of invented details.
- Part 2 is deferred or mostly marked `[INSUFFICIENT INFO]`.

### Inconsistent Input

Input:

```text
Senior Backend Engineer role.
- Need someone with 10+ years experience.
- Must be Mid-Senior level.
- Tech: Java preferred, but we'd also consider .NET.
- Location: Warsaw office mandatory.
- Remote work fully accepted.
- Comp budget: 8-12k PLN gross monthly.
- Project: greenfield enterprise system.
- Existing team to onboard with.
```

Expected:
- Flags contradictions: 10+ years vs Mid-Senior, Java vs .NET, Warsaw mandatory vs remote accepted, seniority vs compensation, greenfield vs existing team.
- Asks collaborative clarification questions.
- Does not silently choose one side.
- Marks affected JD sections as deferred or `[CONFIRM: input was contradictory]`.

### Inclusive Language Audit

Input:

```text
Looking for a young, dynamic engineer to join our high-energy team.
Must be a culture fit - we work hard and play hard.
Recent graduates and digital natives preferred.
He/she will report to our Lead Engineer.
We need a rockstar developer who's passionate about building world-class software.
Tech: any modern web stack.
Location: Warsaw, full-time office.
```

Expected:
- Flags age-coded, gendered, culture-coded, and hype-heavy language.
- Flags `any modern web stack` as too vague.
- Clean draft avoids all risky phrases.
- Uses gender-neutral language.
- Reframes culture fit as role-relevant behaviors.

### Salary Disclosure And EEO Discipline

Input:

```text
Senior DevOps Engineer.
Tech: AWS, Terraform, Kubernetes, GitHub Actions, Datadog.
Years: 6+
Location: Romania remote, occasional Bucharest office visits.
English: C1.
Compensation: 25-32k RON gross monthly.
Process: 2 rounds.
Hiring manager wants to publish to LinkedIn job board.
NOTE: Romania law requires salary disclosure on public job ads as of 2025.
```

Expected:
- Treats compensation as clear and includes the exact supplied range.
- May flag `2 rounds` as needing detail.
- Does not invent salary numbers or add conflicting salary caveats.
- Includes EEO only if official wording is supplied; otherwise marks official EEO as missing.
- Produces public-job-board-appropriate language.

## Scoring

Score expected behaviors as present, absent, or partial. A working v1 should keep at least 85% of expected behaviors and should never fail the sparse-input, contradiction, invented-detail, or inclusive-language checks.
