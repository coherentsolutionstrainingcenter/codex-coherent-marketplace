---
name: cv-format-converter
description: Reformats candidate CVs into a client-ready recruiter presentation format. Use when converting pasted CV text, PDF/DOCX-extracted CV content, or multilingual CV notes into a standardized English profile; supports anonymization levels NONE, NAME-ONLY, and FULL; preserves exact experience, skills, dates, and achievements while flagging missing fields, suspicious patterns, and protected personal data.
---

# CV Format Converter

## Overview

Convert a candidate CV into a client-ready profile draft. The output must preserve the source CV accurately, apply the requested anonymization level, translate non-English content into English when needed, and flag missing information for recruiter follow-up.

Treat every output as a draft. The recruiter must review the converted CV line by line against the source before sending it to a client.

## Required Intake

Before converting, identify:

- Target role.
- Target client or `undisclosed`.
- Anonymization level: `NONE`, `NAME-ONLY`, or `FULL`.
- Source CV content.
- Optional client or company CV template requirements.

If anonymization level or target role is missing, ask for it before producing a client-ready CV. If only the template is missing, use the default structure below and note that the recruiter should map it to the official template.

## Output Contract

Use this default structure unless a supplied template overrides it:

1. `CANDIDATE IDENTIFIER`
2. `HEADLINE / CURRENT ROLE`
3. `SUMMARY` - 3-4 third-person, role-relevant sentences.
4. `KEY SKILLS` - grouped by languages, frameworks, tools, methodologies, cloud, databases, or other relevant categories.
5. `YEARS OF EXPERIENCE BY DOMAIN`
6. `PROJECT HISTORY` - most recent first, with role title, domain or industry, duration, tech stack, responsibilities, and achievements where stated.
7. `EDUCATION`
8. `LANGUAGES`
9. `CERTIFICATIONS`
10. `MISSING FIELDS / GAPS TO CONFIRM`
11. `VALIDATION NOTES`

Use third-person wording and a neutral client-presentation tone. Do not over-market the candidate.

## Anonymization Rules

Apply anonymization exactly:

- `NONE`: keep candidate-provided professional information, but still remove protected or irrelevant personal data.
- `NAME-ONLY`: replace the candidate name with initials or `Candidate A`; keep employer names, education, and location unless the user asks otherwise.
- `FULL`: replace name, remove specific employers, remove specific schools, reduce exact location to country or broad region, remove contact details, and remove photo references.

For `FULL` anonymization, use truthful descriptors instead of names:

- Employer: `European fintech company`, `top-3 Czech bank`, `global IT services company`.
- School: `Tier-1 European technical university`, `Polish technical university`.
- Location: `Poland`, `Czech Republic`, `Central Europe`.

Never anonymize by inventing prestige. If the source does not support `top-tier`, use a neutral descriptor.

## Accuracy Rules

These are mandatory:

- Never fabricate experience, skills, certifications, dates, employers, education, metrics, or seniority.
- Never inflate the CV to fit the target role.
- Do not change `Software Engineer` into `Senior Software Engineer` unless the source says so.
- Preserve specifics such as `AWS Lambda + DynamoDB`, `team of 12`, `15+ services`, or `40% latency reduction`.
- If the target role requires more experience than the source shows, flag the gap instead of hiding it.
- If a required template field is missing, add `[MISSING - recruiter to confirm with candidate]: ...`.
- If source wording is vague, keep it factual and flag it instead of polishing it into stronger claims.

## Translation Rules

- Output in English unless the user asks otherwise.
- If the source CV is non-English, mark `[Translated from Polish]`, `[Translated from Russian]`, or the relevant language at the top.
- Preserve technical terms, product names, certifications, and tool names in their standard form.
- Translate role descriptions accurately without adding implied responsibility.

## Filtering And Quality Flags

Remove protected or irrelevant personal details:

- Age, date of birth, photo descriptions, marital status, children, religion, health, political views, and similar details.
- Nationality should be omitted unless the recruiter frames it as lawful work authorization context. Prefer `work authorization` wording when available.

If filtering occurred, add:

```text
[FILTERED: protected attributes present in source]
```

Flag suspicious or quality-risk patterns neutrally:

- Vague date ranges or inconsistent dates.
- Repeated generic phrasing across roles.
- Overly polished, metric-heavy bullets with no concrete tools or projects.
- Missing technologies for a technical role.

Use:

```text
[VALIDATE - possible quality flag: ...]
```

For possible AI-generated CVs, use:

```text
[POSSIBLE AI-WRITTEN CV - recruiter validates with conversation]
```

## Policy Reminder

End with:

```text
Policy reminder: This is an AI-assisted CV draft. The recruiter must validate every line against the source CV before sending it to a client.
```

## Example Prompts For Recruiters

```text
Use $cv-format-converter to reformat this CV for client presentation.
Target role: Senior Java Backend
Target client: undisclosed fintech
Anonymization: FULL
[paste CV]
```

```text
Use $cv-format-converter to convert this Polish CV into English and apply NAME-ONLY anonymization:
[paste CV]
```

```text
Use $cv-format-converter to identify missing fields against our client CV template before I ask the candidate for updates:
[paste template requirements]
[paste CV]
```

```text
Use $cv-format-converter to anonymize this CV fully. Preserve all technical specifics and flag anything suspicious or inconsistent:
[paste CV]
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It captures regression checks from the original CV Format Converter eval kit, especially anonymization, inflation defense, personal-data filtering, translation, and possible AI-written CV detection.
