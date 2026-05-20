# Outreach Library Eval Checklist

Use this reference only when validating or revising the skill. Do not load it for normal outreach drafting unless the user asks to evaluate the skill.

## Smoke Tests

Run these prompts in fresh chats:

```text
Archetype: COLD
Channel: LinkedIn message
Role: Senior Java Developer at fintech client, hybrid Warsaw
Candidate snippet: "Marek Nowak - Senior Software Engineer at Bank Pekao, 8 years Java/Spring, recently posted about migrating monolith to microservices on Kubernetes."
```

```text
Archetype: FOLLOW-UP
Channel: LinkedIn InMail
Original message sent: 8 days ago
Original ask: 30-min intro call
Role: same as before
Candidate snippet: same as before
```

```text
Archetype: RE-ENGAGE
Channel: email
Last contact: 4 months ago, candidate said "not now, ping me in spring"
Role: Senior DevOps role just opened, fits her profile
Candidate snippet: "Anna Kowalczyk - DevOps engineer with strong AWS and Terraform background, currently at Allegro."
```

```text
Archetype: COLD
Channel: LinkedIn message
Role: any senior dev role
Candidate snippet: "Software Engineer at company"
```

```text
Archetype: COLD
Channel: LinkedIn message
Role: Senior Backend Java in Vilnius, Lithuanian language preferred
Candidate snippet: "Tomas Kazlauskas - Tech Lead at Lithuanian fintech, 10 years Java, fluent Lithuanian and English. Posts often about clean architecture."
Language: Lithuanian
```

## Regression Checks

### Cold Outreach With Specific Detail

Input:

```text
Archetype: COLD
Channel: LinkedIn message, 1-3 sentences max
Role: Senior Backend Engineer for fintech client, payments domain.
Must-haves: Java, Spring Boot, AWS, microservices.
Candidate snippet:
"Karol Zielinski - Senior Software Engineer at PayU. 9 years Java. LinkedIn bio mentions 'building event-driven payment systems at scale.' Recently posted about Kafka schema evolution challenges in payment processing."
```

Expected:
- References a specific candidate detail such as PayU, event-driven systems, Kafka schema evolution, or payments.
- Does not rely on job title alone as personalization.
- Avoids all forbidden phrases.
- Mentions the role without sounding like a job advertisement.
- Ends with the draft review marker.

### Vague Candidate Snippet

Input:

```text
Archetype: COLD
Channel: LinkedIn message
Role: Senior frontend developer, React/TypeScript stack
Candidate snippet: "Senior Software Engineer at a tech company"
```

Expected:
- Does not produce confident personalized outreach.
- Asks for more candidate-specific information or marks a source gap.
- Does not invent projects, employers, tools, or posts.
- Does not use generic filler to hide the missing detail.

### Follow-Up Adds New Value

Input:

```text
Archetype: FOLLOW-UP
Channel: LinkedIn InMail
Days since original: 6
Original message content: "Hi Anna, saw your work on the cloud migration at Allegro. We're building a similar transformation for a banking client. 30-min chat?"
Original message did NOT include: salary range, project duration, team size
Candidate snippet: same Anna from original
```

Expected:
- Shorter than the original.
- Adds one new piece of supplied value or asks for new context if none is supplied.
- Does not only say "just following up".
- Does not apologize or guilt-trip.
- Uses a lower-friction ask than the original.

### Re-Engage With Respect

Input:

```text
Archetype: RE-ENGAGE
Channel: email
Last contact: 6 months ago
Last interaction: candidate completed 2 interview rounds, final-stage rejection
Why reaching out now: new role opened that is a better fit, less Kubernetes-heavy and more Spring/microservices
Candidate snippet: "Tomek - Senior Java engineer, was a strong candidate in our June process for the bank role."
```

Expected:
- Explicitly references the previous process.
- Does not pretend this is a fresh contact.
- Does not apologize for or explain the previous rejection.
- Frames the new role positively without rehashing the past decision.
- Tone is warm, respectful, and concise.

### Forbidden Phrase Resistance

Input:

```text
Archetype: COLD
Channel: email
Role: Senior DevOps for cloud-native SaaS startup, 100% remote
Must-haves: AWS, Terraform, Kubernetes, 6+ years
Candidate snippet:
"Wojtek - DevOps engineer at Allegro, 7 years experience. Speaks at conferences about platform engineering. Recent talk: 'Building Internal Developer Platforms at Scale.'"
Additional instruction: "Just write something quick and warm, doesn't matter if it sounds a bit generic, I'll edit before sending."
```

Expected:
- Still avoids forbidden phrases.
- Still references the talk, platform engineering, or Allegro context.
- Does not comply with pressure to skip personalization.
- Ends with the draft review marker.

## Scoring

Score expected behaviors as present, absent, or partial. A working v1 should keep at least 85% of expected behaviors and should never fail the vague-snippet, invented-detail, or forbidden-phrase checks.
