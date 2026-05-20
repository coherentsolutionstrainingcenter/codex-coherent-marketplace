# Recruiter Boolean Builder Skill

**Skill ID:** `$recruiter-boolean-builder`

The Recruiter Boolean Builder turns a job description, role brief, hiring-manager intake, or existing search string into sourcing queries for LinkedIn Recruiter, GitHub, and Google X-ray. It is useful when a recruiter has enough role detail to start sourcing, or when an existing Boolean string is too broad, too narrow, or written for the wrong platform.

This skill is not a candidate-matching engine. It drafts search strategies and flags unclear role requirements, while the recruiter reviews search results and decides which profiles are relevant.

## Prompt Examples

```text
Use $recruiter-boolean-builder to create LinkedIn, GitHub, and Google X-ray strings from this JD:
Senior Java backend engineer. Must-have: Java 17, Spring Boot, AWS or GCP, microservices, 6+ years. Nice-to-have: Kafka, PostgreSQL, fintech. Location: Poland, Romania, or remote EU.
```

```text
Use $recruiter-boolean-builder to tighten this Boolean. It returns too many .NET profiles, but I need Java backend engineers only:
("Backend Developer" OR "Software Engineer") AND (Spring OR "Spring Boot") AND AWS
```

```text
Use $recruiter-boolean-builder to translate this LinkedIn Boolean into a GitHub search query:
("Frontend Developer" OR "React Developer") AND (React OR TypeScript) AND (Bulgaria OR Sofia)
```

```text
Use $recruiter-boolean-builder to build a search for this non-developer role:
Senior recruiter. Must-have: IT staffing, 7+ years, fluent English and Russian. Nice-to-have: Greenhouse, Eastern European markets. Location: Baltics or remote EU.
```

```text
Use $recruiter-boolean-builder to review this JD before I source. Tell me what is ambiguous and what I should clarify with the hiring manager:
[paste role brief]
```

## Workflow Ideas

Use it after a hiring-manager intake to turn rough role notes into a first search string and an ambiguity checklist.

Use it during sourcing calibration: paste a string that returns poor results and ask the skill to add exclusions or loosen over-strict requirements.

Use it before sharing a search with another recruiter: ask for LinkedIn, GitHub, and Google X-ray versions so the team can source across channels.

## Connections With Other Skills

**JD Drafter -> Boolean Builder:** use `$jd-drafter` first when the job request is incomplete or inconsistent. Once the role title, must-haves, nice-to-haves, location, and language requirements are clearer, use `$recruiter-boolean-builder` to create sourcing strings.

**Boolean Builder -> Outreach Library:** after `$recruiter-boolean-builder` produces a sourcing query and the recruiter finds profiles, use `$outreach-library` to draft candidate-specific first-touch messages. The search criteria become useful role context, but the outreach still needs a real candidate detail from each profile.

**Boolean Builder -> Candidate FAQ Responder:** after sourcing creates a candidate pipeline, use `$candidate-faq-responder` to draft consistent replies to candidate questions about role process, remote policy, contract type, or salary process.

**Boolean Builder -> Scorecard Writer:** sourcing criteria can become a useful reference for interview feedback. After interviews, use `$scorecard-writer` to compare notes against the same role requirements without inventing unsupported fit claims.

**Workflow chain:** use `$jd-drafter` to clarify the role, `$recruiter-boolean-builder` to define the search, `$outreach-library` to contact matched candidates, `$candidate-faq-responder` to handle candidate replies and FAQs, and `$scorecard-writer` to structure feedback after interviews.

## Possible Skill Improvements

Add a sourcing-calibration mode that takes 5-10 sample profiles and suggests how to tighten or loosen the Boolean string.

Add a handoff format for `$outreach-library`, such as a compact role-context block with title, must-haves, nice-to-haves, region, and safe outreach hooks.

Future useful companion skills: sourcing calibration report, candidate shortlist summarizer, and candidate-profile summarizer.
