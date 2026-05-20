---
name: follow-up-finder
description: Identifies candidate follow-up opportunities and drafts short contextual follow-up messages. Use with pasted outreach context, candidate status notes, or connected mailbox search results; supports email, LinkedIn messages, and InMail; never auto-sends; avoids spammy phrases; suggests stopping after two unanswered follow-ups.
---

# Follow-Up Finder

## Overview

Find or draft candidate follow-ups. This skill has two modes:

- **Manual mode**: the recruiter pastes the original message, candidate context, days elapsed, channel, and prior follow-up count.
- **Connected mailbox mode**: when Outlook or another approved mail connector is available and the user asks to find follow-ups, search only mailboxes the user is authorized to access, identify candidate-facing threads with no reply, and draft messages for recruiter review.

Never auto-send follow-ups.

## Required Intake

For manual drafting, use:

- Original outbound message.
- Candidate name or identifier and role.
- Days elapsed since the original message.
- Channel: email, LinkedIn message, or LinkedIn InMail.
- Number of previous follow-ups.
- Optional new information to add.

For connected discovery, use:

- Lookback window, default 5-7 business days if the user does not specify.
- Candidate or role scope if provided.
- Mailbox authorization. Do not inspect shared or other recruiters' mailboxes without explicit user access and request.

## Discovery Output

When finding follow-ups from mail context, return:

1. `FOLLOW-UP CANDIDATES FOUND` - candidate/thread, role if known, last outbound date, days elapsed, and why it appears follow-up eligible.
2. `EXCLUDED THREADS` - internal messages, candidate replies already received, closed roles, or unclear cases.
3. `DRAFT FOLLOW-UPS` - one draft per eligible candidate.
4. `RECRUITER CHECKS BEFORE SENDING` - facts, role status, and tone to verify.

## Drafting Rules

Every follow-up must:

- Acknowledge the gap without sounding passive-aggressive.
- Add one new piece of value or context not present in the previous message.
- Lower friction compared with the original ask.
- Be shorter than the original message.
- Match the channel length.
- End with `DRAFT - recruiter to review before sending.`

Examples of new value:

- Updated role detail.
- New project context.
- A specific safe detail from the candidate profile.
- A simpler ask, such as interest check before scheduling a call.

## Channel Length

- LinkedIn message: 1-3 sentences.
- LinkedIn InMail: 3-5 sentences.
- Email: 4-7 sentences.

## Stop Rule

After two unanswered follow-ups, do not draft a third follow-up unless the user explicitly confirms there is a strong reason. Recommend stopping and moving on.

## Forbidden Phrases

Do not use:

- `I hope this message finds you well`
- `just bumping this up`
- `circling back`
- `touching base`
- `wanted to put this back on your radar`
- `in case you missed this`

## Safety And Privacy Rules

- Do not auto-send.
- Do not imply the candidate has ignored the recruiter intentionally.
- Do not pressure the candidate or create urgency that is not true.
- Do not inspect unauthorized mailboxes.
- Exclude internal Coherent or stakeholder emails unless the user explicitly asks for stakeholder follow-up drafting.
- The recruiter validates role status before sending.

## Example Prompts For Recruiters

```text
Use $follow-up-finder to draft a follow-up. Original message sent 7 days ago, no reply, LinkedIn message, first follow-up:
[paste original outreach]
Candidate: Senior Java engineer with fintech background.
```

```text
Use $follow-up-finder to re-engage a candidate who went silent after the interview. Keep it short and offer an easy next step:
[paste last thread]
```

```text
Use $follow-up-finder to decide whether I should send another follow-up. This would be my third message with no reply:
[paste thread]
```

```text
Use $follow-up-finder to find candidate email threads from the last 7 business days that need follow-up, then draft messages for review.
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It focuses on adding new value, lowering friction, channel length, no third follow-up by default, no forbidden phrases, and no auto-send behavior.
