---
name: outreach-library
description: Drafts specific, human recruiter outreach messages in Coherent-style voice for cold first-touch, warm follow-up, and stale-candidate re-engagement. Use when creating or rewriting LinkedIn messages, LinkedIn InMail, or email outreach from a candidate profile snippet, CV excerpt, prior interaction, role brief, or sourcing context while avoiding generic AI-sounding language, invented candidate details, compensation claims, client names, or confidential project specifics.
---

# Outreach Library

## Overview

Draft candidate outreach that is brief, specific, and safe for recruiter review. Every message must be grounded in candidate-provided context and role facts, then marked as a draft for the recruiter to personalize before sending.

## Intake Decision

Before drafting, classify the request:

- **Cold outreach**: first message to a candidate with no prior contact.
- **Follow-up**: message sent after no reply to a previous outreach, usually 5-10 days later.
- **Re-engage**: message to a stale candidate from a past pipeline or prior conversation, usually after 3+ months.
- **Rewrite**: improve a recruiter draft to be more specific, warmer, shorter, or less AI-sounding.
- **Insufficient candidate detail**: ask for one specific candidate detail before drafting.

If the archetype or channel is missing, infer it only when obvious. Otherwise ask a concise clarifying question.

## Required Inputs

Use these inputs when available:

- Candidate snippet: LinkedIn profile excerpt, CV excerpt, short bio, post, project, employer detail, or prior interaction.
- Role context: job title plus 2-3 must-haves.
- Archetype: `COLD`, `FOLLOW-UP`, or `RE-ENGAGE`.
- Channel: LinkedIn message, LinkedIn InMail, or email.
- Optional: original message, days since contact, prior pipeline context, language, country, recruiter draft, or cleared compensation details.

Do not draft confident outreach from a generic profile like `Software Engineer at company`. Ask for a concrete candidate detail such as a project, post, domain, tool, employer, contribution, or prior conversation point.

## Personalization Rule

Every message must reference one specific detail from the candidate's profile or prior interaction. Do not use job title alone as the specific detail.

Good specific details include:

- A named project, product, migration, platform, domain, or technical challenge.
- A recent post, talk, article, open-source contribution, or portfolio item.
- A company and the concrete work associated with it, not only the company name.
- A previous recruiting conversation, interview stage, or candidate-stated timing preference.

Never invent candidate details to satisfy personalization.

## Archetype Rules

### Cold

Use for first-touch outreach:

- Open with one specific candidate detail.
- Add one sentence on why the role may fit.
- Ask one low-friction question or give one simple call to action.
- Close warmly and briefly with the recruiter name if supplied.

### Follow-Up

Use when the candidate did not reply:

- Acknowledge the timing without apologizing for the follow-up.
- Add exactly one new piece of value or context that was not in the first message, if supplied.
- Lower the friction compared with the original ask.
- Keep it shorter than the original message.

If the user does not provide the original message or new context, ask for it or draft a very short follow-up that does not pretend to know what was previously said.

### Re-Engage

Use when the candidate is from a prior pipeline or went quiet months ago:

- Reference the previous interaction explicitly.
- Explain why the recruiter is reaching out now.
- Do not guilt-trip the candidate or imply they did something wrong by going silent.
- Keep it to 4-6 sentences maximum.

## Channel Length

Match the channel unless the user gives a stricter limit:

- **LinkedIn message**: 2-4 sentences.
- **LinkedIn InMail**: 5-8 sentences.
- **Email**: 8-12 sentences for full cold outreach, shorter for follow-ups or re-engagement.

Do not add padding. The message should feel like something a senior recruiter would actually send.

## Language Rules

- Default to English.
- If the recruiter specifies a language, draft in that language and add `[Language: <language>]` at the top.
- If the recruiter specifies a country where a local language is clearly expected, such as Poland, Lithuania, Romania, Bulgaria, Ukraine, or Georgia, draft in the local language unless the user asks for English.
- If language choice is uncertain, ask before drafting.

## Content Safety Rules

- Never include compensation specifics unless the recruiter provided them and confirmed they are cleared for outreach.
- Never include client names, confidential project details, legal terms, relocation commitments, visa commitments, or internal process details unless explicitly provided and cleared.
- Do not auto-send or imply the message has already been sent.
- Treat the output as advisory under Coherent Solutions PLC064 v1.8 or the user's applicable AI policy. The recruiter validates and personalizes before sending.

## Forbidden Phrases

Do not use these phrases or close variants:

- `I hope this message finds you well`
- `I came across your profile`
- `I was impressed by`
- `incredible opportunity`
- `exciting opportunity`
- `rockstar`
- `ninja`
- `guru`
- `passionate team`
- `exciting journey`
- `game-changer`
- `amazing team`

Also avoid generic filler such as `great fit`, `fast-growing company`, `unique opportunity`, or `quick chat?` unless the surrounding context makes it specific and natural.

## Output Contract

Return:

1. Optional source gap note when needed, such as `Source gap: provide one candidate-specific detail before sending.`
2. Optional language note, such as `[Language: Polish]`.
3. `DRAFT OUTREACH`
4. One draft message only, unless the user asks for variants.
5. `RECRUITER CHECKS BEFORE SENDING` when facts, confidentiality, language, or personalization need review.

End every output with:

```text
DRAFT - recruiter to personalize and review before sending.
```

## Rewrite Rules

When improving a recruiter draft:

- Preserve the recruiter's facts and intent.
- Remove forbidden phrases and generic filler.
- Shorten before adding polish.
- Add candidate-specific detail only when supplied.
- If the original draft lacks personalization, mark the source gap instead of inventing one.

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It captures regression checks from the original Outreach Library eval kit, especially personalization integrity, forbidden-phrase resistance, follow-up value, re-engagement tone, and language handling.
