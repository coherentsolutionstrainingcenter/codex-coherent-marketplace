---
name: recruiter-boolean-builder
description: Builds recruiter Boolean search strings from job descriptions, role briefs, hiring manager intakes, or existing search strings. Use when creating, refining, translating, or troubleshooting sourcing queries for LinkedIn Recruiter, GitHub, and Google X-ray; flags ambiguous requirements before sourcing; supports software engineering, adjacent technical, recruiting, BA, PM, QA, DevOps, data, and other recruiter-led roles.
---

# Recruiter Boolean Builder

## Overview

Turn a job description, role brief, hiring-manager intake, or existing search query into recruiter-ready sourcing strings. Treat outputs as advisory: the recruiter validates search results and candidate relevance.

Default to Coherent Solutions context when the user does not specify another company or market:
- Hiring region: Eastern Europe, the Baltics, the Balkans, and remote EU.
- Common roles: Java, .NET, Python, JavaScript/TypeScript, React, Angular, Node.js, AWS, Azure, GCP, DevOps, QA, BA, PM, Data Engineering, and recruiting roles.
- Search language: English unless the user explicitly requests another language or a country-specific language requirement is a must-have.

## Intake Decision

Before writing strings, classify the request:

- **Fresh search from enough role detail**: produce the standard three search sections.
- **Vague role**: do not invent stack, location, seniority, domain, or language requirements. Ask targeted clarifying questions or list blocking ambiguities.
- **Existing string refinement**: refine the supplied string. If the user refers to a previous string that is not present in context, ask for it or provide concrete edit patterns without pretending to remember it.
- **Translation between platforms**: preserve the user's requirements while adapting syntax to the target platform.
- **Non-technical or non-GitHub-relevant role**: keep the GitHub section, but mark it `Not applicable` with a short reason instead of creating a fake GitHub search.

## Output Contract

For a fresh search with enough information, return exactly three labeled sections:

1. `LinkedIn Recruiter Boolean`
2. `GitHub Search Query`
3. `Google X-ray Search`

For each applicable section:
- Put the search string in a fenced code block, ready to copy.
- Then list:
  - Must-have skills used
  - Nice-to-have skills used
  - Exclusions applied, with short reasons

After the three sections, add:
- `Ambiguities to clarify` when anything material is unclear.
- A short note that the recruiter should validate the search results.

Keep the response concise and practical. Do not explain Boolean logic unless the user asks.

## Query Rules

### LinkedIn Recruiter Boolean

Use `AND`, `OR`, `NOT`, parentheses, and exact-phrase quotes.

- Use 3-5 must-have concept groups joined by `AND`.
- Put synonyms and equivalent titles inside `OR` groups.
- Exclude obvious false positives with `NOT`.
- Avoid over-filtering on nice-to-haves unless the user asks to narrow aggressively.
- Treat preferred location, local presence, certifications, and domain background as soft filters unless marked mandatory.

Example shape:

```text
("Java Developer" OR "Java Engineer" OR "Backend Engineer") AND ("Spring Boot" OR Spring) AND (AWS OR GCP) AND (microservices OR "distributed systems") NOT (.NET OR "C#" OR "ASP.NET")
```

### GitHub Search Query

Use GitHub-native syntax where useful: `language:`, `location:`, `followers:`, `repos:`, `stars:`, `in:bio`, `in:readme`.

- Use this mainly for engineering, DevOps, data, QA automation, and open-source-heavy roles.
- Prefer one primary `language:` for software roles when obvious.
- Use `location:` only when the role has a clear geographic target.
- Use `in:bio` or `in:readme` for framework, cloud, or domain terms.
- Mark `Not applicable` for roles where GitHub is unlikely to index useful profiles, such as recruiters or business stakeholders.

### Google X-ray Search

Use `site:linkedin.com/in/` as the base.

- Combine title, stack, location, and domain terms with browser-friendly Boolean operators.
- Include regional or location terms when provided.
- Keep the query short enough to paste into Google without becoming brittle.

Example shape:

```text
site:linkedin.com/in/ ("Java Developer" OR "Java Engineer") ("Spring Boot" OR Spring) (AWS OR GCP) (Poland OR Romania OR "remote EU") -".NET" -"C#"
```

## Ambiguity Handling

Flag ambiguity when role information is missing, conflicting, or too broad. Common blockers:

- Technology stack or core tools are missing.
- Must-have versus nice-to-have is unclear.
- Seniority is undefined or inconsistent with years of experience.
- Location, remote policy, relocation, timezone, or language requirement is unclear.
- Role family is unclear, such as full-stack versus backend, manual QA versus automation QA, BA versus product owner.
- Domain requirement may be too strict or unrealistic.

For unusably vague input, ask 3-6 targeted questions instead of producing strings.

## Safety And Recruiting Judgment

- Do not claim that any candidate is or is not a fit.
- Do not infer protected traits or add filters for age, gender, nationality, ethnicity, disability, family status, religion, or visa status.
- If the user asks for a "native speaker", translate that into role-relevant language proficiency such as fluent or professional-level language skill and flag the wording if useful.
- Do not fabricate client names, countries, tools, levels, or prior context.
- For multilingual roles, only require a language when the prompt says it is required. If language is preferred, put it in nice-to-have or clarify.
- Treat the output as governed by the user's recruiting and AI-use policies. The search string is drafted by AI; the recruiter judges the results.

## Example Prompts For Recruiters

Use these examples when demonstrating the skill to new recruiters:

```text
Use $recruiter-boolean-builder to build LinkedIn, GitHub, and Google X-ray searches from this JD:
Senior Java backend engineer for a fintech client. Must-have: Java 17+, Spring Boot, microservices, AWS or GCP, 6+ years. Nice-to-have: Kafka, PostgreSQL, financial services experience. Location: Poland, Romania, or remote EU. English C1+.
```

```text
Use $recruiter-boolean-builder to tighten this LinkedIn Boolean. It returns too many .NET profiles, but I need Java only:
("Backend Developer" OR "Software Engineer") AND (Spring OR "Spring Boot") AND AWS
```

```text
Use $recruiter-boolean-builder to translate this LinkedIn Boolean into a GitHub search query:
("Frontend Developer" OR "React Developer") AND (React OR TypeScript) AND (Bulgaria OR Sofia)
```

```text
Use $recruiter-boolean-builder for a non-developer role:
Senior recruiter for our internal HR team. Must-have: 7+ years agency or in-house recruiting, IT staffing experience, fluent English and Russian. Nice-to-have: Eastern European market knowledge, Greenhouse or similar ATS. Location: Lithuania, Latvia, Estonia, or remote.
```

```text
Use $recruiter-boolean-builder and tell me what you need before searching:
Need a developer urgently.
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It captures regression checks from the original Boolean Builder eval kit.
