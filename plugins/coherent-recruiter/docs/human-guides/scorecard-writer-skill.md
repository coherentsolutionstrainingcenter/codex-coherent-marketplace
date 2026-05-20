# Scorecard Writer Skill

**Skill ID:** `$scorecard-writer`

The Scorecard Writer turns rough recruiter notes, dictated notes, transcript excerpts, or draft feedback into a structured candidate scorecard in English. It is designed for evidence-based interview feedback: it should use what the recruiter actually wrote, flag thin evidence, and avoid invented ratings or final hiring decisions.

This skill is especially useful after prescreens, technical interviews, or combined interviewer feedback. The recruiter remains responsible for validating, editing, and submitting the final scorecard.

## Prompt Examples

```text
Use $scorecard-writer to turn these interview notes into a draft scorecard:
Interviewed Maria for Senior Java. Strong Spring Boot, gave 3 project examples. Kafka limited. Communication clear. Asked good team-structure questions. Notice 4 weeks. Salary expectation 18-22k PLN gross.
```

```text
Use $scorecard-writer to translate these Russian notes into an English scorecard and flag anything that needs validation:
[paste Russian interview notes]
```

```text
Use $scorecard-writer to refine this draft scorecard so it is more balanced, evidence-based, and neutral:
[paste draft feedback]
```

```text
Use $scorecard-writer to convert this Teams transcript into structured candidate feedback. Do not invent English level or technical depth:
[paste transcript excerpt]
```

```text
Use $scorecard-writer to handle conflicting interviewer feedback and clearly show what the recruiter needs to reconcile:
[paste feedback from two interviewers]
```

## Workflow Ideas

Use it immediately after an interview while the recruiter's notes are fresh. Dictated notes are enough if they include concrete evidence.

Use it after a technical interviewer sends unstructured feedback. The skill can separate strengths, concerns, technical assessment, communication, and next steps.

Use it as a quality-control step before submitting a scorecard: ask it to flag unsupported claims, missing evidence, and risky personal details.

## Connections With Other Skills

**JD Drafter -> Scorecard Writer:** use the validated requirements from `$jd-drafter` as role context when writing interview feedback, especially when the original JR was incomplete or contradictory.

**Boolean Builder -> Scorecard Writer:** use the original role requirements from `$recruiter-boolean-builder` as context when writing role fit, so feedback stays aligned with the search criteria.

**Outreach Library -> Scorecard Writer:** once a candidate who was contacted through `$outreach-library` completes a prescreen or interview, use `$scorecard-writer` to convert rough notes into structured feedback.

**Scorecard Writer -> Candidate FAQ Responder:** after the recruiter validates the scorecard, use `$candidate-faq-responder` to draft a candidate update or rejection message. Only share feedback details that the recruiter approves and company policy allows.

**Workflow chain:** `$jd-drafter` clarifies role requirements, `$recruiter-boolean-builder` defines sourcing criteria, `$outreach-library` starts candidate contact, `$candidate-faq-responder` manages candidate questions during the process, and `$scorecard-writer` captures evidence after interviews.

## Possible Skill Improvements

Add a handoff mode that produces a short, safe candidate-update summary for `$candidate-faq-responder` without exposing sensitive scorecard details.

Add role-specific scorecard templates for common technical roles, QA, BA, PM, recruiting, and DevOps while keeping evidence rules unchanged.

Future useful companion skills: interview question generator, candidate summary for hiring managers, rejection-feedback policy checker, and ATS update writer.
