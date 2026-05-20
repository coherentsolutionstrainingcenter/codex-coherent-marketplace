# Outreach Library Skill

**Skill ID:** `$outreach-library`

The Outreach Library drafts candidate outreach messages that sound like they came from a senior recruiter rather than a generic AI template. It supports cold first-touch messages, warm follow-ups, and re-engagement messages for stale candidates across LinkedIn messages, LinkedIn InMail, and email.

The skill is built around one rule: every outreach draft needs one real, specific candidate detail. If the profile snippet is too vague, the skill should ask for more context instead of inventing personalization. This makes it useful for recruiters who want faster messaging without losing credibility with candidates.

## Prompt Examples

```text
Use $outreach-library to draft a cold LinkedIn message:
Role: Senior Java Developer, fintech client, hybrid Warsaw.
Must-haves: Java, Spring Boot, AWS, microservices.
Candidate: Marek Nowak - Senior Software Engineer at Bank Pekao, 8 years Java/Spring, recently posted about migrating a monolith to microservices on Kubernetes.
```

```text
Use $outreach-library to write a follow-up InMail that is shorter than my first message and uses a lower-friction ask:
Original ask: 30-minute intro call.
Days since original: 7.
New context I can share: the team is open to candidates who prefer hybrid work in Warsaw.
[paste original message and candidate snippet]
```

```text
Use $outreach-library to re-engage this candidate from last year:
Last contact: candidate said "not now, ping me in spring."
Role now: Senior DevOps, AWS and Terraform.
Candidate: Anna Kowalczyk - DevOps engineer at Allegro, strong AWS/Terraform background.
Channel: email.
```

```text
Use $outreach-library to rewrite my draft so it sounds less like AI and keeps one candidate-specific detail:
[paste draft]
[paste candidate snippet]
```

```text
Use $outreach-library to draft this outreach in Lithuanian:
Role: Senior Backend Java in Vilnius.
Candidate: Tomas Kazlauskas - Tech Lead at a Lithuanian fintech, 10 years Java, posts about clean architecture.
Channel: LinkedIn message.
```

## Workflow Ideas

Use it immediately after sourcing. Once a search produces promising profiles, paste the candidate snippet and role context to create a first-touch message.

Use it as a quality-control pass for recruiter-written outreach. Ask it to remove forbidden phrases, shorten the message, and preserve candidate-specific context.

Use it for follow-up discipline. Paste the original message plus one new value point, then ask for a shorter, lower-friction follow-up.

Use it to revive old pipelines. Provide the last interaction and why the role is relevant now, then draft respectful re-engagement.

Use it for multilingual outreach when the recruiter knows the target language or country and needs a concise first draft.

## Connections With Other Skills

**JD Drafter -> Outreach Library:** use `$jd-drafter` to clarify the role and produce a clean role brief before drafting outreach. This helps keep first-touch messages aligned with validated must-haves instead of rough intake notes.

**Boolean Builder -> Outreach Library:** use `$recruiter-boolean-builder` to create sourcing strings, then use `$outreach-library` once real candidate snippets are available.

**Outreach Library -> Candidate FAQ Responder:** after candidates reply, use `$candidate-faq-responder` to answer repeated questions about salary process, contract type, remote work, hiring steps, or policy details.

**Outreach Library -> Scorecard Writer:** once a candidate responds and completes a prescreen or interview, use `$scorecard-writer` to turn interview notes into structured feedback.

**Workflow chain:** `$jd-drafter` clarifies the role, `$recruiter-boolean-builder` creates the search, `$outreach-library` drafts the first message and follow-ups, `$candidate-faq-responder` handles candidate questions during the process, and `$scorecard-writer` structures post-interview feedback.

## Possible Skill Improvements

Add anonymized examples of "good" and "bad" recruiter outreach to sharpen the voice. The current skill already has a forbidden-phrase list, but real team examples would make it more consistent.

Add language-specific reference examples for Polish, Lithuanian, Romanian, Bulgarian, Ukrainian, and Georgian outreach if recruiters will use those languages often.

Connect this skill later with a future candidate-profile summarizer so recruiters can turn pasted profiles into a clean candidate snippet before drafting.
