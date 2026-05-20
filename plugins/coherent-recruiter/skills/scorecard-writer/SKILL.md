---
name: scorecard-writer
description: Turns rough recruiter interview notes, dictated notes, draft feedback, or pasted meeting transcripts into structured, evidence-based candidate scorecards in English. Use when Codex needs to draft, refine, translate, or rebalance interview feedback while avoiding invented facts, unsupported competency ratings, final hiring decisions, and protected or bias-risk personal details.
---

# Scorecard Writer

## Overview

Draft structured candidate scorecards from raw interview notes. Inputs may be bullets, voice-dictated text, Russian or English notes, Teams transcript excerpts, interviewer feedback, or a rough scorecard draft.

Treat every output as a recruiter-owned draft. The recruiter must validate evidence, edit the text, and own the final hiring decision.

## Intake Decision

Before drafting, classify the input:

- **Enough interview evidence**: produce a full draft scorecard.
- **Sparse notes**: ask for more detail or produce a minimal scorecard with most sections marked `[VALIDATE - limited evidence in notes]`.
- **Russian or mixed-language notes**: output in English and mark `[Translated from Russian]` or `[Partially translated from Russian]` near the top.
- **Draft scorecard refinement**: preserve the recruiter's facts, improve structure and balance, and flag unsupported claims.
- **Conflicting interviewer feedback**: surface both views and mark `[FEEDBACK CONFLICT - recruiter to reconcile]`.
- **Transcript input**: summarize only what is relevant to the role and cite the notes when making strong claims.

## Output Contract

For a full scorecard, use these sections in this order:

1. `CANDIDATE SUMMARY` - 2-3 neutral sentences.
2. `ROLE FIT` - one paragraph against the role or JD. If no JD is provided, say what can and cannot be assessed.
3. `STRENGTHS` - 3-5 bullets, each tied to specific evidence from the notes.
4. `CONCERNS / GAPS` - 3-5 bullets, each tied to specific evidence or explicitly marked as not assessed.
5. `TECHNICAL ASSESSMENT` - include only when technical questions, tools, or examples appear in the notes.
6. `SOFT SKILLS / COMMUNICATION` - include only when visible in the notes.
7. `PRACTICAL DETAILS` - include only when process-relevant logistics appear, such as notice period, availability, location, work model, salary expectation, or current compensation if the user's hiring policy permits it.
8. `DRAFT RECOMMENDATION` - clearly marked as draft and phrased for recruiter validation.
9. `SUGGESTED NEXT STEPS` - examples: clarify missing evidence, second interview, technical screen, hiring-manager review, or decline draft for recruiter review.
10. `VALIDATION NOTES` - include required caveats, filtered-data note, and policy reminder.

If there is too little evidence, do not create a confident-looking full scorecard. Ask targeted follow-up questions or provide a short draft where unsupported sections say `Not assessed in this interview`.

## Evidence Rules

These rules are mandatory:

- Never invent details that are not in the notes.
- Never invent candidate name, role title, seniority, English level, technical depth, motivation, compensation, or availability.
- Never assign ratings, levels, or competency scores unless the notes explicitly provide them.
- If English level is not mentioned, write `Not assessed in this interview`.
- Quote the notes for strong claims. Use: `Per notes: "[exact quote]".`
- If a section is thin on evidence, write `[VALIDATE - limited evidence in notes]`.
- Preserve the recruiter's intended distinction between strong, weak, theoretical, production, preferred, and required experience.
- When notes conflict, do not choose a side. Represent both perspectives and require recruiter reconciliation.

## Recommendation Rules

- Never make a final hire or no-hire decision.
- Use cautious language such as `Based on the notes provided, the candidate appears to...`.
- State what the recruiter should validate before submitting the scorecard.
- If the notes support a next step, phrase it as a draft recommendation, not a decision.
- If the evidence is sparse or conflicting, recommend clarification rather than progression or rejection.

## Translation Rules

- Output should be in English unless the user explicitly asks otherwise.
- Translate Russian notes into clear English while preserving the recruiter's intent.
- Mark translated outputs with `[Translated from Russian]` or `[Partially translated from Russian]`.
- If a phrase is ambiguous, ask for clarification instead of guessing.

## Filtering And Bias Controls

Filter protected or bias-risk personal details that are not role-relevant. Do not repeat the sensitive detail in the scorecard.

Filter examples:
- Age or date of birth.
- Marital status, children, pregnancy, parental leave, family plans.
- Photo descriptions, appearance, disability, religion, ethnicity, nationality, or similar protected attributes.
- Same alma mater, personal similarity to the interviewer, or vague `culture fit` claims without behavioral evidence.

At the end, add a generic note when filtering occurred:

```text
[FILTERED: protected attributes or bias-risk details were present in the source notes and were excluded from the scorecard.]
```

Compensation, notice period, availability, location, and work model may be included under `PRACTICAL DETAILS` when the recruiter supplied them and they are relevant to the recruiting process. Do not infer or embellish them.

## Tone

Use a professional, neutral, evidence-based tone. Avoid generic praise and superlatives such as `amazing` or `outstanding` unless the notes use those exact terms. Prefer clear, specific wording over polished but vague AI-speak.

## Policy Reminder

End with a concise reminder:

```text
Policy reminder: This is an AI-assisted draft. The recruiter must validate every conclusion, edit the scorecard before submission, and own the final hiring decision.
```

If the user's organization uses Coherent Solutions PLC064 v1.8 or another named AI policy, refer to that policy in the reminder when relevant.

## Example Prompts For Recruiters

Use these examples when demonstrating the skill to new recruiters:

```text
Use $scorecard-writer to turn these interview notes into a draft scorecard:
Interviewed Maria for senior Java role.
- Strong on Spring Boot, mentioned 3 specific projects.
- Hesitated on Kafka questions, said she has only used it briefly.
- Communication clear, asked good questions about team structure.
- Wants to start in 4 weeks, current notice 2 weeks plus PTO.
- Salary expectation: 18-22k PLN gross/month.
```

```text
Use $scorecard-writer to translate these Russian notes into an English scorecard:
Ivan, Senior Java. 8 years of experience. Strong Spring knowledge. Built microservices from scratch. English B2, speaks confidently. Does not know Kafka, ready to learn. Salary 24k PLN. Can start in one month.
```

```text
Use $scorecard-writer to refine this draft feedback so it is more balanced and evidence-based:
[paste draft scorecard or rough feedback]
```

```text
Use $scorecard-writer to convert this Teams transcript into structured candidate feedback. Flag any section where the evidence is thin:
[paste transcript excerpt]
```

```text
Use $scorecard-writer to handle conflicting interviewer feedback:
Interviewer 1 says code quality was strong and communication clear. Interviewer 2 says the candidate seemed defensive when challenged. Both agree the technical level is senior.
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It captures regression checks from the original Scorecard Writer eval kit, especially sparse-note hallucination defense, translation handling, personal-data filtering, and conflicting feedback.
