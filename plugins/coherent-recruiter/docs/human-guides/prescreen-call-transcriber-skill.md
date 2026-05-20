# Prescreen Call Transcriber Skill

**Skill ID:** `$prescreen-call-transcriber`

The Prescreen Call Transcriber structures raw prescreen transcripts, dictated notes, or third-party transcription output into recruiter-ready notes. It captures candidate background, role-fit strengths and gaps, language assessment, practical details, candidate questions, and follow-up items.

This skill does not record audio. Recruiters must handle call recording consent and provide transcript text or notes.

## Prompt Examples

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
Use $prescreen-call-transcriber to identify which prescreen questions were not covered:
[paste question list]
[paste transcript]
```

```text
Use $prescreen-call-transcriber to flag inconsistencies between the candidate's stated experience and the CV excerpt:
[paste CV excerpt]
[paste transcript]
```

## Workflow Ideas

Use it immediately after a prescreen call when the recruiter has transcript text or dictated notes.

Use it before writing a formal scorecard. The prescreen summary can become structured input for `$scorecard-writer`.

Use it to identify missing information while the candidate is still warm: salary, notice period, English level, location, work authorization, or must-have experience.

## Connections With Other Skills

**JD Drafter -> Prescreen Call Transcriber:** use the validated JD or role brief from `$jd-drafter` as context when structuring prescreen notes and identifying what the recruiter still needs to clarify.

**Prescreen Call Transcriber -> Scorecard Writer:** use the structured prescreen notes as input for `$scorecard-writer` when a formal feedback record is needed.

**Prescreen Call Transcriber -> Candidate FAQ Responder:** if the candidate asked questions during the call, use `$candidate-faq-responder` to draft accurate follow-up answers from the FAQ.

**Candidate Relevance Ranker -> Prescreen Call Transcriber:** after `$candidate-relevance-ranker` identifies high-priority candidates, this skill helps document the first human conversation.

Future useful companion skills: consent script generator, prescreen question generator, ATS notes formatter, and follow-up email drafter.
