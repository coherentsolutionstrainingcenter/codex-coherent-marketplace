# CV Format Converter Skill

**Skill ID:** `$cv-format-converter`

The CV Format Converter turns a candidate CV into a client-ready profile draft. It standardizes structure, applies the requested anonymization level, translates non-English CV content into English, preserves exact professional details, and flags missing fields or suspicious patterns.

This skill is accuracy-first. It should not make a candidate look stronger than the source CV supports. The recruiter must validate every line before sending the result to a client.

## Prompt Examples

```text
Use $cv-format-converter to reformat this CV for client presentation.
Target role: Senior Java Backend
Target client: undisclosed fintech
Anonymization: FULL
[paste CV]
```

```text
Use $cv-format-converter to translate and reformat this Polish CV into English.
Anonymization: NAME-ONLY
Target role: Senior Frontend Engineer
[paste CV]
```

```text
Use $cv-format-converter to check what is missing from this CV before I ask the candidate for updates:
[paste client CV template fields]
[paste CV]
```

```text
Use $cv-format-converter to fully anonymize this CV. Preserve all technologies, metrics, dates, and achievements exactly:
[paste CV]
```

```text
Use $cv-format-converter to reformat this CV and flag possible AI-written or low-specificity sections:
[paste CV]
```

## Workflow Ideas

Use it after a candidate agrees to be presented to a client. Convert the source CV into a clean draft, then compare it line by line against the original.

Use it before client submission to check missing fields: English level, availability, work authorization, project dates, or exact tech stack.

Use it when anonymization requirements differ by client. The recruiter can run the same CV through NAME-ONLY and FULL anonymization for different submission contexts.

## Connections With Other Skills

**JD Drafter -> CV Format Converter:** use the validated role requirements from `$jd-drafter` to decide which source-CV details are role-relevant, while still preserving only facts present in the original CV.

**Boolean Builder -> CV Format Converter:** sourcing criteria from `$recruiter-boolean-builder` can help emphasize role-relevant skills without inventing missing experience.

**CV Format Converter -> Candidate Relevance Ranker:** once CVs are standardized, `$candidate-relevance-ranker` can compare them more consistently against a JD.

**CV Format Converter -> Candidate FAQ Responder:** if missing fields require candidate follow-up, use `$candidate-faq-responder` to draft a concise request for clarification.

Future useful companion skills: client submission email writer, CV template formatter for DOCX, anonymization policy checker, and missing-field follow-up assistant.
