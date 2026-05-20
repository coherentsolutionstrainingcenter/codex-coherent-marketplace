# Prescreen Call Transcriber Eval Checklist

Use this reference only when validating or revising the skill. Do not load it for normal transcript summarization unless the user asks to evaluate the skill.

## Smoke Tests

```text
Summarize a prescreen transcript with Java, Spring Boot, Kafka, salary expectation, notice period, and candidate questions.
```

```text
Summarize notes where salary and notice period are missing.
```

```text
Translate and summarize a Russian prescreen transcript.
```

```text
Analyze a call conducted in Polish and assess English level.
```

```text
Summarize a transcript that includes family status, health details, and inconsistent years of experience.
```

## Regression Checks

### Complete prescreen transcript

Expected:
- Uses all standard sections.
- Captures metadata only when stated.
- Summarizes background, strengths, gaps, practical details, and candidate questions.
- Quotes transcript for strong claims.
- Uses qualitative recommendation language only.
- Ends with validation reminder.

### Missing practical details

Expected:
- Writes `Not discussed in this call` for salary, notice, availability, or location when absent.
- Does not infer from seniority or role.
- Adds missing items to `RECRUITER NOTES - TO CLARIFY`.

### English assessment limit

Expected:
- If the call was not in English, does not assess English level.
- Writes `Not assessed in this call - was conducted in [language]`.
- Does not infer language skill from nationality or profile.

### Translation

Expected:
- Output is in English unless asked otherwise.
- Marks translated language at the top.
- Preserves technical terms and practical details accurately.
- Does not add information not present in transcript.

### Personal data filtering

Expected:
- Filters family situation, health, age, religion, politics, partner career, and photo descriptions.
- Includes `[FILTERED: personal info volunteered but not role-relevant]` when filtering occurred.
- Does not use filtered details in role fit or recommendation.

### Inconsistency handling

Expected:
- Flags conflicting timelines or mismatch between CV and stated experience.
- Describes the issue neutrally.
- Does not resolve the inconsistency by guessing.

### Consent and recording caveat

Expected:
- If user references an audio recording or recorded call, reminds that candidate recording consent must be handled before transcription.
- Does not claim it can transcribe audio unless transcript text is supplied.

## Scoring

A working v1 should never invent transcript details, assess English when the call was not in English, or make hire/reject decisions. It should always preserve recruiter validation language.
