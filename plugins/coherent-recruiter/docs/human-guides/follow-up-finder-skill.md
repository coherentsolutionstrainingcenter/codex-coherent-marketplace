# Follow-Up Finder Skill

**Skill ID:** `$follow-up-finder`

The Follow-Up Finder helps recruiters identify and draft follow-ups for candidates who have not replied, went silent mid-process, or have not confirmed an interview slot. It can work from pasted thread context, and in a connected environment it can search authorized mailbox context.

The skill drafts messages only. The recruiter reviews and sends manually.

## Prompt Examples

```text
Use $follow-up-finder to draft a first LinkedIn follow-up. Original message sent 7 days ago, no reply:
[paste original message]
Candidate context: Senior Java engineer, fintech background.
```

```text
Use $follow-up-finder to re-engage this candidate who went silent after interview scheduling:
[paste thread]
```

```text
Use $follow-up-finder to decide whether I should send another follow-up. This would be my third unanswered message:
[paste thread]
```

```text
Use $follow-up-finder to find candidate email threads from the last 7 business days that may need follow-up, then draft messages for review.
```

## Workflow Ideas

Use it twice a week to clear stale candidate conversations.

Use it after sourcing campaigns to write second-touch messages that add new value instead of repeating the first outreach.

Use it after interview scheduling when candidates have not confirmed a slot.

## Connections With Other Skills

**Recruiter Boolean Builder -> Follow-Up Finder:** after sourcing campaigns, use this skill to keep candidate replies moving.

**Candidate FAQ Responder -> Follow-Up Finder:** if candidates ask questions and then go silent, combine FAQ-grounded answers with a concise follow-up.

**Follow-Up Finder -> Pipeline Report Generator:** repeated silent candidates or stage stalls can become pipeline risk signals.

Future useful companion skills: Outlook follow-up automation, LinkedIn campaign reviewer, candidate re-engagement sequence builder, and ATS stale-status finder.
