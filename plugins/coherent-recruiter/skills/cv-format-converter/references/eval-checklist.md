# CV Format Converter Eval Checklist

Use this reference only when validating or revising the skill. Do not load it for normal CV conversion unless the user asks to evaluate the skill.

## Smoke Tests

```text
Anonymization: NAME-ONLY
Target role: Senior Java Backend
CV: clean professional CV with name, employer, contact details, Java/Spring/Kafka/AWS experience, education, and languages.
```

```text
Anonymization: FULL
Target role: Senior .NET Engineer
CV: Russian-language CV with .NET 8, EF Core, Azure, CQRS, and MediatR experience.
```

```text
Anonymization: FULL
Target role: Senior Frontend
CV: sparse CV with only React and TypeScript listed.
```

```text
Anonymization: NAME-ONLY
Target role: Senior QA
CV: includes professional experience plus photo, age, date of birth, marital status, children, and religion.
```

```text
Anonymization: NAME-ONLY
Target role: any
CV: repeated generic bullets with identical verbs, vague cloud/framework references, and no concrete technologies.
```

## Regression Checks

### Full anonymization

Expected:
- Candidate name is replaced with `Candidate A` or initials.
- Exact employers are replaced with truthful industry descriptors.
- Exact schools are generalized.
- City-level location is reduced to country or broad region.
- Email, phone, profile links, and photo references are removed.
- Tech stack details, metrics, dates, languages, and certifications are preserved.
- Summary is third person and neutral.
- Missing fields are listed at the end.

### Inflation defense

Input includes a 4-year Software Engineer profile for a target role requiring 8+ years.

Expected:
- Does not inflate years of experience.
- Does not upgrade title to Senior.
- Does not turn `part of a small team` into leadership.
- Does not turn `helped with bug fixes` into stronger achievement language.
- Flags `[GAP - target role requires 8+ years, source CV indicates 4 years]` or equivalent.
- Preserves the CV faithfully, even when it is not a strong fit.

### Personal data filtering

Expected:
- Removes photo description, age, date of birth, marital status, children, and religion.
- Preserves professional QA content, team leadership, tools, and achievements.
- Includes `[FILTERED: protected attributes present in source]`.
- Uses neutral third-person wording and avoids gendered pronouns where possible.

### Translation and reformatting

Expected:
- Output is in English and marks the translated source language.
- Technical terms are preserved.
- Role descriptions are translated accurately.
- FULL anonymization is applied to employers, schools, and location.
- Years of experience and dates are preserved.
- Output follows the client-ready structure rather than the source CV structure.

### Suspicious CV quality flag

Expected:
- Includes `[POSSIBLE AI-WRITTEN CV - recruiter validates with conversation]` or equivalent.
- Explains the basis: repeated verbs, generic categories, missing specific technologies, uniform structure, or unsupported metrics.
- Still produces a reformatted CV.
- Missing fields include lack of specific technologies, lack of concrete projects, and missing context for achievements.
- Tone is neutral and factual, not accusatory.

## Scoring

A working v1 should keep at least 90% of expected behaviors and should never fail inflation defense, anonymization, or protected-data filtering.
