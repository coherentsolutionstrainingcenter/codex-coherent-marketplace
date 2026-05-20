# Job Request Gap Analyzer Eval Checklist

Use this reference only when validating or revising the skill. Do not load it for normal JR analysis unless the user asks to evaluate the skill.

## Smoke Tests

```text
Analyze a JR with clear Java, Spring Boot, AWS, Senior level, Poland, and two interview rounds.
```

```text
Analyze a JR that says Senior in the title but 3+ years in requirements.
```

```text
Analyze a JR that says urgent but gives no start date, budget, location, or interview process.
```

```text
Analyze a Russian JR and draft the clarification message in Russian.
```

```text
Draft a clarification message with 14 missing fields.
```

## Regression Checks

### Complete JR

Expected:
- Marks answered fields as `CLEAR`.
- Does not ask questions already answered.
- May include minor ambiguities, but does not invent gaps.
- Draft message is short or says no blocking questions remain.

### Incomplete JR

Expected:
- Flags missing seniority, must-haves, location, remote policy, budget, start date, and interview process when absent.
- Gives a specific stakeholder question for each blocker.
- Prioritizes 6-8 sourcing blockers in the draft message.
- Defers lower-priority questions if there are too many.

### Inconsistency handling

Expected:
- Surfaces contradictions such as Senior title with 3+ years.
- Asks for confirmation instead of choosing one side.
- Keeps the tone collaborative.

### No fabricated details

Expected:
- Does not infer seniority from salary, infer location from client, or create a tech stack from the role title.
- Uses `MISSING` or `AMBIGUOUS` when the JR does not state something.

### Language matching

Expected:
- If the JR is in Russian or another clear language, drafts the clarification in that language and marks it.
- Does not switch language without reason.

### No auto-send

Expected:
- Drafts a message only.
- Includes recruiter review language.
- Does not imply sending has happened.

## Scoring

A working v1 should never ask questions already answered, fabricate JR facts, or auto-send. It should prioritize sourcing blockers clearly.
