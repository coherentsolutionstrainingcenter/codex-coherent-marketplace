---
name: job-request-gap-analyzer
description: Analyzes incomplete or inconsistent job requests from Delivery Managers or hiring stakeholders, checks them against standard recruiter intake fields, and drafts specific clarification questions. Use when reviewing a JR, ATS field dump, email brief, or role request before sourcing; flags missing fields, ambiguous requirements, contradictions, and sourcing blockers without fabricating details or auto-sending messages.
---

# Job Request Gap Analyzer

## Overview

Analyze a job request before sourcing begins. Identify which details are clear, ambiguous, or missing, then draft a concise clarification message for the recruiter to send to the stakeholder.

The recruiter remains the sender. This skill drafts, but never sends, stakeholder communication.

## Required Intake

The user may provide:

- Job request text, ATS fields, Word content, or stakeholder email.
- Stakeholder name and role, if known.
- Recruiter notes about suspected gaps.
- Optional standard JR template or required fields.

If the role request is too thin to analyze, ask for the original JR or the stakeholder context before drafting a message.

## Output Contract

Return two parts in this order.

## Part 1 - Gap Analysis

Use the standard fields below unless a supplied template overrides them. For each field, mark one of:

- `CLEAR` - well-defined in the input.
- `AMBIGUOUS` - present but unclear, conflicting, or open to multiple interpretations.
- `MISSING` - not present in the input.

For every `AMBIGUOUS` or `MISSING` item, include:

- One-line reason.
- One specific question for the stakeholder.

Standard JR fields:

- Role title and seniority level.
- Project or client, or anonymization level if undisclosed.
- Start date and urgency, including what urgent means in days.
- Project duration for staffing roles.
- Must-have technical skills, top 3-5.
- Nice-to-have technical skills.
- Years of experience expected.
- Domain or industry experience required.
- Tech stack specifics, versions, frameworks, tools.
- Team size and team composition.
- Reporting line and team structure.
- Location and time zone requirements.
- Remote, hybrid, or on-site policy.
- Language requirements.
- Compensation band or note that it will not be disclosed.
- Interview process, rounds, and interviewers.
- Decision-makers on the client side.
- Special requirements such as clearance, certifications, travel, or on-call.

## Part 2 - Draft Clarification Message

Draft an email or Teams message back to the stakeholder.

For email, include:

```text
Subject: Quick clarifications on the [role] JR
```

Message structure:

- Warm, brief opening that acknowledges the JR.
- Grouped questions by category: role and seniority, tech stack, practical details, and process.
- Maximum 6-8 questions in the main message.
- Prioritize sourcing blockers: must-haves, seniority, location, budget, urgency, interview process.
- Put lower-priority deferred questions at the end if needed.
- Close with a specific next step, such as `Once I have these, I can start sourcing on [date]` or offer a 15-minute call.

## Question Rules

- Never fabricate JR details.
- Never ask a question that is already answered in the input.
- Keep questions specific. Prefer `Should this be Mid-level (4-7 years) or Senior (8+ years)?` over `What level?`.
- Flag inconsistencies clearly. Example: `The JR says Senior but lists 3+ years. Could you confirm the target seniority?`
- Keep tone collaborative, not bureaucratic.
- Match the JR language when obvious. If drafting in Russian, Polish, or another language, mark `[Drafted in Russian]` or equivalent at the top.

## Safety And Workflow Rules

- Do not auto-send or imply the message has been sent.
- Do not over-audit the stakeholder. The goal is to unblock sourcing.
- If more than 8 questions are needed, say which questions are sourcing blockers and which can be clarified later.
- The recruiter must review and personalize the message before sending.

## Example Prompts For Recruiters

```text
Use $job-request-gap-analyzer to analyze this JR and draft clarification questions for the Delivery Manager:
[paste JR]
```

```text
Use $job-request-gap-analyzer to compare this role request against our standard intake fields and show what blocks sourcing:
[paste role request]
```

```text
Use $job-request-gap-analyzer to draft a Teams message to Alex, Delivery Manager. Keep it collaborative and limit it to the most important questions:
[paste incomplete JR]
```

```text
Use $job-request-gap-analyzer to analyze this Russian JR and draft the clarification message in Russian:
[paste JR]
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It focuses on missing-field detection, not asking already answered questions, inconsistency handling, question prioritization, language matching, and no auto-send behavior.
