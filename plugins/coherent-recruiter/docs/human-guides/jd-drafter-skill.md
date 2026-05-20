# JD Drafter Skill

**Skill ID:** `$jd-drafter`

The JD Drafter turns hiring manager intake notes, incomplete job requests, existing JDs, or rough role briefs into a structured job-description draft. Its main value is not just writing the JD; it first shows what is clear, missing, or contradictory so recruiters can ask better questions before publishing.

This skill is designed for recruiter workflows where accuracy matters. It should not invent client names, compensation, team size, technology versions, project timelines, interview process, or legal/EEO boilerplate. If a detail is missing, the skill marks it as a gap and gives a specific question to ask the Delivery Manager or hiring manager.

## Prompt Examples

```text
Use $jd-drafter to analyze this hiring manager intake and draft a JD:
Role: Senior Backend Engineer
Project: e-commerce platform for a Polish retail client, anonymize as "Top-3 Polish retailer"
Tech: Java 17, Spring Boot 3, PostgreSQL, AWS, Kafka
Team: 8 engineers, 1 PM, 1 architect
Location: Warsaw or remote within Poland
English: B2+
Start: ASAP, ideally within 4 weeks
Process: HR screen, tech interview, system design, final with hiring manager
```

```text
Use $jd-drafter to tell me what is missing before I go back to the Delivery Manager:
Need a senior Java developer for a banking client. ASAP.
```

```text
Use $jd-drafter to audit this request for contradictions and draft only the sections that are safe:
Senior Engineer, 10+ years required.
Mid-Senior, 3-5 years.
Java preferred, but .NET is also fine.
Warsaw office mandatory, but fully remote accepted.
```

```text
Use $jd-drafter to rewrite this JD in a more inclusive, specific, candidate-friendly voice. Preserve facts and flag unsupported claims:
[paste existing JD]
```

```text
Use $jd-drafter to create a non-technical JD:
Senior Recruiter for internal People team.
Must-have: 7+ years agency or in-house recruiting, IT staffing, fluent English and Russian.
Location: Lithuania-based or remote Baltics.
Reports to Head of TA.
```

## Workflow Ideas

Use it before writing a JD from scratch. Paste rough intake notes and use the gap analysis as the checklist for follow-up questions.

Use it after receiving a low-quality JR. The skill can separate what is usable from what needs clarification, which is faster than manually rewriting the whole request.

Use it as a legal and quality guardrail before publishing. Ask it to audit an existing JD for invented details, inclusive-language issues, missing salary disclosure, or unsupported claims.

Use it as a training demo for recruiters. Compare "draft a JD" against "analyze gaps first, then draft" using the same sparse input to show why prompt structure matters.

## Connections With Other Skills

**JD Drafter -> Recruiter Boolean Builder:** once `$jd-drafter` clarifies must-haves, nice-to-haves, location, and language requirements, use `$recruiter-boolean-builder` to generate sourcing strings.

**JD Drafter -> Outreach Library:** after the JD is validated, use `$outreach-library` to turn the role context into candidate-specific first-touch messages.

**JD Drafter -> Candidate Relevance Ranker:** use the cleaned JD as the role brief for `$candidate-relevance-ranker` when comparing incoming profiles or sourced candidates.

**JD Drafter -> Scorecard Writer:** use the validated JD requirements as context when `$scorecard-writer` structures interview feedback.

**Full workflow:** `$jd-drafter` clarifies the role, `$recruiter-boolean-builder` creates search strings, `$outreach-library` drafts candidate messages, `$candidate-faq-responder` handles candidate questions, `$prescreen-call-transcriber` structures screening notes, and `$scorecard-writer` creates evidence-based feedback.

## Sharing With Recruiters

For a team of 17 recruiters, the easiest starting point is to share two things:

1. The skill package: `jd-drafter-skill.zip`
2. This usage guide: `jd-drafter-skill.md`

Each recruiter who uses Codex can install the skill by unzipping the package into their local Codex skills folder:

```text
~/.codex/skills/jd-drafter
```

After that, they can invoke it in Codex with:

```text
Use $jd-drafter to analyze this job request and draft a JD:
[paste job request]
```

For training, give recruiters a 20-minute exercise: first run a sparse request like `Need a senior Java developer for a banking client. ASAP.`, then run a complete intake. The contrast shows why the gap-analysis step is the main feature.

## Distribution Notes

The `.zip` package is enough for manual distribution through Slack, Teams, SharePoint, or email. For a larger rollout, store the skill folders in a shared internal repository or SharePoint folder and version them there, so everyone can update from the same source.

Do not put private client names, real compensation policy, or legal boilerplate into a widely shared package unless it is approved for that audience. If the team has official JD templates, "About us" text, benefits language, and EEO statement, those can be added later as reference files after approval.

## Possible Skill Improvements

Add approved Coherent JD boilerplate as reference files: About Coherent, What We Offer, EEO statement, and country-specific salary-disclosure language.

Add role-family templates for Java, .NET, Frontend, DevOps, QA, BA, PM, Data, and Recruiting roles.

Add a Delivery Manager question generator that exports only the missing/ambiguous items from Part 1 as a concise message.
