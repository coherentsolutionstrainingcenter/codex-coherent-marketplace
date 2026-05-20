# Candidate FAQ Responder Skill

**Skill ID:** `$candidate-faq-responder`

The Candidate FAQ Responder drafts warm, brief, candidate-facing replies for repeated recruiter questions on email, LinkedIn messages, and LinkedIn InMail. It works best when the recruiter provides the candidate message plus a trusted FAQ, policy excerpt, role brief, or recruiter-approved facts.

This skill is intentionally cautious. If the candidate asks about salary ranges, benefits, remote eligibility, relocation, visa support, legal status, client names, project details, or timelines and the FAQ does not cover it, the skill should ask the recruiter to confirm instead of guessing.

## Prompt Examples

```text
Use $candidate-faq-responder to draft a LinkedIn reply. Use only this FAQ excerpt:
[paste salary-process FAQ]

Candidate: "Hi! What's your usual salary range for senior Java roles?"
```

```text
Use $candidate-faq-responder to answer this in Polish. Do not invent rates:
[paste contract/rate FAQ]

Candidate: "Czesc, czy oferujecie B2B czy tylko UoP? I czy stawki sa negocjowalne?"
```

```text
Use $candidate-faq-responder to write a polite rejection email:
Candidate: Marek
Role: Senior Frontend
Stage: after prescreen
Reason: role requires React/Next.js, while Marek's recent experience is mainly Vue/Nuxt.
```

```text
Use $candidate-faq-responder to respond to this frustrated candidate email. Keep it human, do not make excuses, and include a recruiter-owned next step:
[paste email]
```

```text
Use $candidate-faq-responder to check whether this question is covered by our FAQ. If it is not, draft a holding response and list what I need to confirm:
[paste FAQ]
[paste candidate question]
```

## Workflow Ideas

Use it as a shared replacement for personal message-template folders. Recruiters can paste the same FAQ source and get consistent candidate answers.

Use it after a candidate asks a policy question. The skill can draft a response and list what must be verified before sending.

Use it for sensitive follow-ups: frustrated candidates, delayed updates, re-engagement, and rejection messages where tone matters.

Use it for multilingual candidate replies when the recruiter needs a short, accurate answer in the candidate's language.

## Connections With Other Skills

**Outreach Library -> Candidate FAQ Responder:** after `$outreach-library` generates first-touch or follow-up outreach, candidates may reply with questions about salary process, remote setup, contract type, timeline, or the hiring process. Use this skill to answer from approved FAQ or policy context.

**Boolean Builder -> Candidate FAQ Responder:** after sourcing starts, candidates often ask about process, location, contract type, and salary. Use this skill to keep replies consistent across the team.

**Scorecard Writer -> Candidate FAQ Responder:** after interview feedback is validated, use this skill to draft a candidate update or rejection. Keep the response concise and avoid sharing unsupported or sensitive scorecard details.

**Four-skill workflow:** use `$recruiter-boolean-builder` to create the search, `$outreach-library` to draft outreach and follow-ups, `$candidate-faq-responder` to manage candidate questions during screening, and `$scorecard-writer` to structure feedback after interviews.

## Possible Skill Improvements

Add a maintained FAQ reference file with approved answers for compensation process, contract type, remote work, relocation, visa support, benefits, and hiring timelines.

Add a handoff mode from `$outreach-library` that preserves the candidate's original question and the role context so FAQ replies stay consistent with the first message.

Future useful companion skills: interview scheduling assistant, FAQ knowledge-base maintainer, and rejection-feedback policy checker.
