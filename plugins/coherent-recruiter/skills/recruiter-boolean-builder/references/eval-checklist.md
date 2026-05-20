# Boolean Builder Eval Checklist

Use this reference only when validating or revising the skill. Do not load it for normal Boolean-string generation unless the user asks to evaluate the skill.

## Smoke Tests

Run these prompts in fresh chats:

```text
Senior Java backend developer. Spring Boot. AWS. Banking domain. Poland or remote EU.
```

```text
Need a developer urgently.
```

```text
Senior business analyst with healthcare experience. Must know SQL, Power BI, and have led requirements gathering for clinical systems. UK or remote EU. Native English speaker preferred.
```

```text
Frontend developer needed in Bulgaria, must speak Bulgarian and English. React, TypeScript, 5+ years.
```

```text
We need a senior DevOps engineer who has 10+ years of experience, must have worked at FAANG, must hold AWS Solutions Architect Professional certification, must have built CI/CD pipelines for fintech regulated environments, must speak fluent English, French, and German, must be willing to relocate to Warsaw, must be available within 2 weeks, and must have led a team of at least 8 engineers.
```

## Regression Checks

### Standard backend role

Input:

```text
Senior Java backend engineer for a fintech client.
Must-have: Java 17+, Spring Boot, microservices, AWS or GCP, 6+ years.
Nice-to-have: Kafka, PostgreSQL, financial services experience.
Location: Poland, Romania, or remote EU. English C1+.
```

Expected:
- Exactly three labeled search sections: LinkedIn, GitHub, Google X-ray.
- Every applicable search string is in a code block.
- LinkedIn uses `AND`, `OR`, and parentheses.
- GitHub uses `language:Java` or an equivalent native filter.
- Google X-ray starts with `site:linkedin.com/in/`.
- Must-have, nice-to-have, and exclusion lists follow the strings.
- The answer reminds the recruiter to validate results.
- No fabricated location names or client names.

### Vague input

Input:

```text
Need a senior developer for our project.
```

Expected:
- Do not produce speculative Boolean strings.
- Ask clarifying questions or flag multiple ambiguities.
- Include at least three of: technology stack, location, seniority definition, must-haves, English level, role context, project domain.
- Do not invent a tech stack.
- Keep the tone collaborative.

### Non-developer role

Input:

```text
Senior recruiter for our internal HR team.
Must-have: 7+ years agency or in-house recruiting, IT staffing experience, fluent English and Russian.
Nice-to-have: Eastern European market knowledge, Greenhouse or similar ATS.
Location: Lithuania, Latvia, Estonia, or remote.
```

Expected:
- LinkedIn uses recruiting-relevant titles such as recruiter, talent acquisition, and sourcer.
- GitHub is marked not applicable or omitted only if the output contract for the tested version permits omission.
- Google X-ray targets LinkedIn with recruiting terms.
- English and Russian fluency are treated as requirements.
- Do not generate a GitHub developer-style query for recruiters.

### Multilingual context

Input:

```text
Senior frontend engineer in Sofia, Bulgaria. React 18, TypeScript, 5+ years.
Bulgarian language not required (team works in English) but local presence preferred.
```

Expected:
- Include Bulgaria/Sofia targeting.
- Do not require Bulgarian.
- Keep output in English unless asked otherwise.
- Treat local presence as preferred, not mandatory.
- Do not assume visa or relocation status.

### Refinement request

Input:

```text
The Boolean string you built for me yesterday is returning too many .NET developers when I need Java only. Tighten it.
```

Expected:
- Ask for the original string because it is not in the current context, or explain concrete `NOT` exclusions for `.NET`, `C#`, and `ASP.NET`.
- Do not invent the previous string.
- Keep the response collaborative.

## Scoring

Score expected behaviors as present, absent, or partial. A working v1 should keep at least 80% of expected behaviors and should never fail the vague-input or hallucinated-refinement checks.
