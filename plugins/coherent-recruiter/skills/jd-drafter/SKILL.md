---
name: jd-drafter
description: Drafts recruiter-ready job descriptions from hiring manager intake notes, incomplete job requests, existing JDs, or rough role briefs. Use when Codex needs to analyze missing or inconsistent JD/JR information, generate clarification questions for Delivery Managers or hiring managers, rewrite a JD in Coherent-style voice, or produce a structured JD while avoiding invented client names, compensation, tech versions, team details, timelines, and non-inclusive language.
---

# JD Drafter

## Overview

Create job descriptions from rough recruiter or hiring-manager input. Always perform intake gap analysis before drafting so missing or contradictory information is visible before a JD becomes a polished public document.

Treat every output as a recruiter-owned draft. The recruiter must validate the gap analysis and the final JD with the hiring manager or Delivery Manager before publishing.

## Intake Decision

Before writing, classify the request:

- **Complete intake**: produce gap analysis, then a full draft JD using supplied evidence.
- **Sparse intake**: make gap analysis the main output and mark role-specific JD sections as insufficient rather than fabricating details.
- **Inconsistent intake**: surface contradictions and defer or mark affected JD sections until resolved.
- **Existing JD rewrite**: preserve facts, remove generic or risky language, and flag unsupported claims.
- **Inclusive language audit**: identify exclusionary, age-coded, gendered, culture-coded, or hype-heavy phrases and rewrite safely.
- **Non-technical role**: keep the same gap-analysis discipline, adapting responsibilities and must-haves to the role family.

If the user asks only "draft a JD" from weak input, still start with gap analysis.

## Output Contract

Return two artifacts in this order:

```text
PART 1 - INTAKE GAP ANALYSIS
```

Then:

```text
PART 2 - DRAFT JOB DESCRIPTION
```

End with:

```text
DRAFT - recruiter and hiring manager to validate before publishing.
```

If the input is too sparse or contradictory to draft responsibly, Part 2 may contain only safe universal sections and `[INSUFFICIENT INFO - see Part 1]` markers.

## Part 1 - Intake Gap Analysis

Use this standard checklist. For each field, mark `CLEAR`, `MISSING`, or `AMBIGUOUS`, then add the evidence or a specific clarification question.

- Role title and seniority level.
- Must-have skills, top 3-5.
- Nice-to-have skills.
- Years of experience expectation.
- Tech stack specifics, including versions and frameworks.
- Domain or industry experience.
- Location, time zone, and remote/hybrid policy.
- Language requirements, including English level and any local language.
- Team size and team composition.
- Reporting line.
- Project duration for contract or staffing roles.
- Client name disclosure: named, anonymized, or undisclosed.
- Compensation band or disclosure policy.
- Interview process steps.
- Start date and urgency.
- Official JD boilerplate: About company, What we offer, and EEO statement.

Write clarification questions that a recruiter can send directly to the Delivery Manager. Prefer specific questions over generic ones.

Example:

```text
AMBIGUOUS - Start date / urgency: "ASAP" is not operationally clear.
Question: Do we need someone within 2 weeks, 4 weeks, or can we consider candidates with a standard 1-2 month notice period?
```

## Part 2 - Draft Job Description

Use this structure:

1. `Role Overview` - 2-3 specific sentences.
2. `About Coherent / About the Project` - use supplied official boilerplate or mark missing.
3. `Responsibilities` - 5-8 bullets grounded in the input.
4. `Must-Have Skills` - 5-7 bullets grounded in the input.
5. `Nice-to-Have Skills` - 3-5 bullets when supplied.
6. `What We Offer` - use supplied official boilerplate or mark missing.
7. `Equal Opportunity Statement` - use supplied official EEO text exactly or mark missing.

If a section cannot be drafted from supplied evidence, write:

```text
[INSUFFICIENT INFO - see Part 1: <field name>]
```

Do not hide missing information behind polished generic text.

## Non-Negotiable Accuracy Rules

- Never invent client names. If the input says `banking client`, write `a banking client` or another safe anonymized phrase.
- Never invent compensation numbers. If compensation is absent, state the field is missing or use the user's supplied disclosure policy.
- Never invent technology versions, team sizes, reporting lines, project duration, interview steps, start dates, or office policy.
- Never silently choose one side of a contradiction. Mark affected fields as `AMBIGUOUS` and ask a clarification question.
- If legal or market-specific salary disclosure is mentioned by the user, follow the supplied instruction exactly and do not add conflicting caveats.
- Do not claim the JD is final or ready to publish.

## Inclusive Language Rules

Use inclusive, candidate-trustworthy language:

- Use gender-neutral language such as `they`, `the engineer`, or `the person in this role`.
- Replace age-coded phrases such as `young`, `digital native`, or `recent graduate preferred` with role-relevant experience requirements.
- Replace vague `culture fit` language with specific collaboration, communication, ownership, or delivery expectations.
- Avoid hype and AI-sounding phrases: `world-class`, `best-in-class`, `rockstar`, `ninja`, `guru`, `passionate journey`, `high-energy`, `work hard play hard`, `exciting opportunity`, and `game-changer`.
- Do not include requirements tied to protected characteristics.

When auditing an existing JD, explicitly list risky language and then provide a cleaned draft.

## Boilerplate Handling

Use official company boilerplate only when the user supplies it or the repository includes a trusted reference. This is especially important for:

- About Coherent / About the company.
- What we offer.
- EEO statement.
- Benefits.
- Compensation disclosure language.

If official boilerplate is unavailable, mark it as a source gap. Do not write a fake legal statement and present it as official.

## Tone

Use professional, specific, honest language. Prefer concrete role facts over marketing copy. Keep bullets scannable and candidate-facing.

## Policy Reminder

When the output is intended for external publication, include a concise reminder:

```text
Policy reminder: This is an AI-assisted draft. The recruiter and hiring manager must validate every section before publishing externally.
```

If the user's organization uses Coherent Solutions PLC064 v1.8 or another named AI policy, refer to that policy when relevant.

## Example Prompts For Recruiters

Use these examples when demonstrating the skill to new recruiters:

```text
Use $jd-drafter to analyze this hiring manager intake and draft a JD:
[paste intake notes]
```

```text
Use $jd-drafter to tell me what is missing before I ask the Delivery Manager follow-up questions:
Need a senior Java developer for a banking client. ASAP.
```

```text
Use $jd-drafter to rewrite this JD in a more specific and inclusive voice. Preserve facts and flag anything unsupported:
[paste existing JD]
```

```text
Use $jd-drafter to audit this JR for contradictions before I publish it:
Senior Engineer, 10+ years. Mid-Senior, 3-5 years. Warsaw mandatory, fully remote accepted. Java or .NET.
```

```text
Use $jd-drafter to draft a non-technical JD for this internal recruiting role:
[paste role brief]
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It captures regression checks from the original JD Drafter eval kit, especially sparse-input hallucination defense, contradiction detection, inclusive language cleanup, salary disclosure handling, and EEO source discipline.
