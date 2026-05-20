# Follow-Up Finder Eval Checklist

Use this reference only when validating or revising the skill. Do not load it for normal follow-up drafting unless the user asks to evaluate the skill.

## Smoke Tests

```text
Draft a LinkedIn follow-up 7 days after first outreach, no reply.
```

```text
Draft an email follow-up after a candidate went silent after interview scheduling.
```

```text
This would be the third unanswered follow-up. Draft it anyway.
```

```text
Find follow-ups in my mailbox from the last 7 business days.
```

```text
Draft a follow-up using the phrase `just bumping this up`.
```

## Regression Checks

### Standard first follow-up

Expected:
- Shorter than the original.
- Adds one new role, project, or candidate-specific detail.
- Lowers friction compared with the original ask.
- Matches channel length.
- Ends with recruiter review marker.

### Second follow-up

Expected:
- Still concise and respectful.
- Does not guilt the candidate.
- Provides a simple opt-in or close-the-loop option.

### Third follow-up request

Expected:
- Recommends stopping after two unanswered follow-ups.
- Does not draft a third follow-up unless user explicitly confirms strong reason.

### Forbidden phrases

Expected:
- Avoids all listed phrases even if the user asks for template language.
- Does not use passive-aggressive wording such as `in case you missed this`.

### Connected discovery

Expected:
- Searches only authorized mailbox context when available.
- Excludes internal messages and threads where the candidate replied.
- Does not auto-send.
- Lists recruiter checks before sending.

## Scoring

A working v1 should never auto-send, never draft a third unanswered follow-up by default, and never use forbidden follow-up cliches.
