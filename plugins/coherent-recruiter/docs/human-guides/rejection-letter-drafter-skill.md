# Rejection Letter Drafter Skill

**Skill ID:** `$rejection-letter-drafter`

The Rejection Letter Drafter creates respectful, legally safer candidate rejection messages from recruiter notes and interviewer feedback. It calibrates detail by stage, channel, and tone so candidates receive appropriate feedback without risky language.

This skill is especially useful after technical interviews and final rounds, where candidates invested time and expect a human, specific response.

## Prompt Examples

```text
Use $rejection-letter-drafter to draft a STAGE 3 rejection email.
Candidate: Marek
Role: Senior Frontend
Tone: STANDARD
Feedback: strong Vue/Nuxt background, but role requires deeper React/Next.js production experience.
```

```text
Use $rejection-letter-drafter to synthesize this feedback from three interviewers. If there is conflict, flag it before drafting:
[paste feedback]
```

```text
Use $rejection-letter-drafter to write a brief STAGE 1 CV-review decline. Keep it kind and do not include detailed reasons.
```

```text
Use $rejection-letter-drafter to draft a final-round rejection with a warm stay-in-touch tone:
[paste approved feedback]
```

## Workflow Ideas

Use it after the recruiter has approved the actual rejection reason.

Use it to consolidate multiple interviewer notes into one candidate-facing message.

Use it as a compliance check for rejection language before sending.

## Connections With Other Skills

**Scorecard Writer -> Rejection Letter Drafter:** validated scorecard evidence can provide safe, role-fit feedback for rejection messages.

**Prescreen Call Transcriber -> Rejection Letter Drafter:** prescreen notes can support a Stage 2 rejection when the candidate is not aligned with the role.

**Candidate FAQ Responder -> Rejection Letter Drafter:** use FAQ-style tone and policy grounding for candidate follow-up questions after rejection.

Future useful companion skills: rejection-policy checker, ATS disposition note writer, talent-pool message drafter, and interviewer feedback reconciler.
