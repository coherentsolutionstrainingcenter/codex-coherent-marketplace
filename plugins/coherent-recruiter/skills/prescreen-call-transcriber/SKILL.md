---
name: prescreen-call-transcriber
description: Structures raw prescreen call transcripts, dictated recruiter notes, or third-party transcription output into recruiter-ready prescreen summaries. Use for candidate background, role-fit strengths and gaps, language assessment, practical details, candidate questions, and follow-up clarification points while preserving transcript evidence, filtering irrelevant personal data, and avoiding hire/reject decisions.
---

# Prescreen Call Transcriber

## Overview

Turn raw prescreen transcript text or rough recruiter notes into a structured prescreen summary. This skill does not record or transcribe audio directly; it works from text produced by Teams, dictation, Whisper, another transcription tool, or manual notes.

The recruiter must verify consent for any recorded call and validate the final summary against the transcript or notes before filing it in the ATS.

## Required Intake

The user may provide:

- Raw transcript or rough notes.
- Job description or role brief.
- Standard prescreen question list.
- Transcript source, date, duration, and call language if known.

If no transcript or notes are supplied, ask for them. If the user asks to process a recording, explain that the skill needs transcript text and that recording consent must be handled before transcription.

## Output Contract

Use these sections in order:

1. `CALL METADATA`
   - Date, duration, language, transcript source, and consent status if stated.
2. `CANDIDATE BACKGROUND`
   - 3-5 bullets on current role, experience, domain, and recent work where stated.
3. `ROLE FIT - STRENGTHS`
   - Specific skills or experience matching the JD when provided.
4. `ROLE FIT - GAPS`
   - Must-haves not addressed or areas where evidence appears thin.
5. `LANGUAGE ASSESSMENT`
   - Assess English only if the call was in English or the transcript contains enough English speech.
6. `PRACTICAL DETAILS`
   - Salary expectations, notice period, availability, location, remote or hybrid preferences, work authorization where disclosed.
7. `CANDIDATE QUESTIONS / CONCERNS`
8. `RECRUITER NOTES - TO CLARIFY`
9. `RECOMMENDATION FOR REVIEW`
10. `VALIDATION NOTES`

## Recommendation Language

Use only qualitative recruiter-review language:

- `Strong evidence of fit - recommend advancing to next round for recruiter validation`
- `Mixed evidence - recruiter to weigh additional context`
- `Weak evidence based on this call - recruiter to confirm whether to advance`

Never make a hire/reject decision.

## Evidence Rules

- Never invent details not present in the transcript or notes.
- If salary, notice period, location, or availability was not discussed, write `Not discussed in this call`.
- Quote the transcript for strong claims using `Per transcript: "..."`.
- If the JD is supplied, compare against it. If not, write what can be assessed and what cannot.
- If information is missing from the call but important for the role, put it in `RECRUITER NOTES - TO CLARIFY`.
- Flag inconsistencies neutrally. Do not resolve them by assumption.

## Language Assessment Rules

- Assess English with CEFR framing only when the call was conducted in English or enough English is visible in the transcript.
- If the call was not in English, write `Not assessed in this call - was conducted in [language].`
- List other languages only when the candidate stated them or the transcript clearly shows them.
- Do not infer language level from nationality, location, or role seniority.

## Filtering And Compliance Rules

Remove personal data not relevant to role suitability:

- Family situation, health, age, religion, political views, partner career, photo descriptions, and similar details.

If filtering occurred, add:

```text
[FILTERED: personal info volunteered but not role-relevant]
```

Flag sensitive workflow constraints:

- Recorded candidate calls require appropriate consent before transcription.
- The GPT output is a summary draft, not the source of truth.
- EU AI Act high-risk recruitment scope means the recruiter owns validation and decisions.

## Neutral Risk Flags

Describe concerns factually. Do not label them as `red flags`.

Examples:

- `The candidate gave a high-level answer on Kubernetes and did not describe production use.`
- `The stated Java timeline appears inconsistent: 5 years in one answer, since 2015 in another.`
- `The CV says Kafka, but the call only confirmed brief exposure.`

## Translation Rules

- Output in English unless the user asks otherwise.
- Translate non-English transcripts into English and mark `[Translated from Russian]`, `[Translated from Polish]`, or the relevant language.
- Preserve exact quoted evidence in the original language when useful, then translate briefly.

## Example Prompts For Recruiters

```text
Use $prescreen-call-transcriber to structure this prescreen transcript into recruiter notes. Compare it against the JD and list what I need to clarify:
[paste JD]
[paste transcript]
```

```text
Use $prescreen-call-transcriber to convert these dictated notes into a prescreen summary. Do not invent salary, notice period, or English level:
[paste notes]
```

```text
Use $prescreen-call-transcriber to translate this Russian transcript into English and summarize candidate background, practical details, and gaps:
[paste transcript]
```

```text
Use $prescreen-call-transcriber to identify what was not covered from our prescreen question list:
[paste question list]
[paste transcript]
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It focuses on transcript grounding, missing practical details, English assessment limits, personal-data filtering, inconsistency flags, and consent reminders.
