---
name: rejection-letter-drafter
description: Drafts respectful, legally safer candidate rejection messages from recruiter notes and interviewer feedback. Use for CV-stage declines, post-prescreen rejections, technical interview rejections, final-round declines, or pipeline-hold messages; calibrates detail by stage, tone, and channel while avoiding protected characteristics, culture-fit language, interviewer names, unsupported feedback, and impersonal AI-tell phrases.
---

# Rejection Letter Drafter

## Overview

Draft candidate rejection messages that are humane, specific enough for the stage, and legally safer. The recruiter must validate and personalize every message before sending.

If interviewer feedback conflicts in a material way, do not draft the candidate-facing message until the recruiter reconciles the conflict.

## Required Intake

Ask for or use:

- Candidate name or `Candidate`.
- Role.
- Rejection stage: `STAGE 1`, `STAGE 2`, `STAGE 3`, `STAGE 4`, or `STAGE 5`.
- Raw feedback from interviewer(s).
- Channel: email or LinkedIn.
- Tone preset: `BRIEF`, `STANDARD`, or `DETAILED`.
- Language, default English.

## Stage Calibration

- `STAGE 1 - CV review`: brief and kind. Do not give specific reasons. Reference interest in the company or role.
- `STAGE 2 - After prescreen`: brief but warmer. Reference the conversation generally and provide one role-fit reason.
- `STAGE 3 - After technical interview`: more detailed. Include 1-2 strengths and one specific role-fit reason.
- `STAGE 4 - Final round`: warmest and most detailed. Include 2-3 strengths, acknowledge the time invested, and provide one constructive role-fit reason.
- `STAGE 5 - Pipeline hold`: not a rejection. Make clear this means `not now`, not `no`, and set a realistic revisit expectation if policy allows.

## Tone Presets

- `BRIEF`: 2-3 short paragraphs.
- `STANDARD`: 3-4 paragraphs.
- `DETAILED`: 4-5 paragraphs with more specific feedback.

Respect channel length. LinkedIn should be shorter than email.

## Compliance Rules

- Never reference protected characteristics: age, gender, nationality, family status, religion, disability, sexual orientation, parental status, marital status, health, or similar attributes.
- Never use `culture fit` as a rejection reason.
- Never include interviewer names.
- Never promise future opportunities unless the recruiter provides approved data-retention or talent-pool language.
- Never reference AI in the candidate-facing message.
- Never write feedback the source does not support.
- If feedback mentions communication, phrase it as role-specific requirement alignment, not personal deficiency.

## Conflict Handling

When feedback from multiple interviewers conflicts materially:

- Return `[FEEDBACK CONFLICT - recruiter to reconcile]`.
- Summarize the conflicting points for the recruiter.
- Ask for the final approved reason before drafting.

Do not silently choose one interviewer view.

## Required Language Patterns

Avoid these phrases:

- `I hope this message finds you well`
- `We regret to inform you`
- `you weren't selected`
- `you didn't meet our criteria`
- `not a culture fit`

Prefer direct human openings, such as:

```text
Thank you for the time you spent with us on the [role] process.
```

End with:

```text
DRAFT - recruiter to review and personalize before sending.
```

## Example Prompts For Recruiters

```text
Use $rejection-letter-drafter to draft a STAGE 3 rejection email.
Candidate: Marek
Role: Senior Frontend
Tone: STANDARD
Feedback: strong Vue/Nuxt background, but role requires deeper React/Next.js production experience.
```

```text
Use $rejection-letter-drafter to synthesize this feedback from three interviewers. If there is a conflict, flag it before drafting:
[paste feedback]
```

```text
Use $rejection-letter-drafter to write a brief STAGE 1 decline for a CV review. Keep it kind and do not include detailed reasons.
```

```text
Use $rejection-letter-drafter to draft a final-round rejection with a warm stay-in-touch tone, but only if the source feedback supports it:
[paste feedback]
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It focuses on stage calibration, safe feedback language, conflict handling, forbidden phrases, no protected characteristics, and recruiter personalization.
