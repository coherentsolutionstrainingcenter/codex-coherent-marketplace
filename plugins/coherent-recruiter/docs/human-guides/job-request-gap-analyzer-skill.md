# Job Request Gap Analyzer Skill

**Skill ID:** `$job-request-gap-analyzer`

The Job Request Gap Analyzer reviews a job request before sourcing starts. It checks whether the JR contains the details recruiters need, flags missing or inconsistent fields, and drafts a concise clarification message for the Delivery Manager or stakeholder.

This skill is for unblocking intake, not criticizing the stakeholder. The recruiter reviews the questions and sends the final message manually.

## Prompt Examples

```text
Use $job-request-gap-analyzer to analyze this JR and draft clarification questions for the Delivery Manager:
[paste JR]
```

```text
Use $job-request-gap-analyzer to identify what blocks sourcing in this role request:
[paste ATS field dump]
```

```text
Use $job-request-gap-analyzer to draft a Teams message to Alex. Limit it to the 6 most important sourcing blockers:
[paste incomplete JR]
```

```text
Use $job-request-gap-analyzer to analyze this Russian JR and draft the clarification message in Russian:
[paste JR]
```

## Workflow Ideas

Use it immediately after receiving a new JR, before opening sourcing or Boolean-building work.

Use it before a 15-minute intake call to prepare targeted questions for the stakeholder.

Use it as a quality gate before `$recruiter-boolean-builder`, so Boolean strings are based on clarified must-haves rather than guesses.

## Connections With Other Skills

**Job Request Gap Analyzer -> Recruiter Boolean Builder:** once missing must-haves, location, seniority, and language requirements are clarified, use `$recruiter-boolean-builder` to create sourcing strings.

**Job Request Gap Analyzer -> JD Drafter:** clarified JR details can feed a cleaner external job description.

**Job Request Gap Analyzer -> Pipeline Report Generator:** if many JRs repeatedly miss the same fields, `$pipeline-report-generator` or a future analytics skill can report intake-quality trends.

Future useful companion skills: intake-call question generator, stakeholder message drafter, JR quality dashboard, and JD consistency checker.
