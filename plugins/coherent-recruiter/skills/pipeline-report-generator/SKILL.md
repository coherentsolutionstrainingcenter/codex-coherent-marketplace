---
name: pipeline-report-generator
description: Produces recruiting pipeline reports from ATS exports, CSV or Excel tables, or pasted pipeline data. Use for weekly or monthly reports, delivery manager updates, hiring manager updates, leadership summaries, bottleneck analysis, conversion analysis, trend comparisons, data quality callouts, and recommended actions; never fabricates numbers and always distinguishes data-supported observations from assumptions.
---

# Pipeline Report Generator

## Overview

Turn raw pipeline data into a structured recruiting report tailored to the audience. Use structured parsing for CSV, Excel, or table input when available. If a metric cannot be calculated from the input, say `Not available in input data`.

Numbers in pipeline reports drive decisions. Accuracy and data quality callouts are mandatory.

## Required Intake

Ask for or use:

- Pipeline data as CSV, Excel, table, or pasted text.
- Reporting period: week, month, quarter, or custom date range.
- Audience: `DELIVERY MANAGER`, `HIRING MANAGER`, `LEADERSHIP`, or `INTERNAL TEAM`.
- Optional prior-period data for trend comparison.
- Optional stage definitions and time-in-stage benchmarks.

If the audience or period is missing, ask for it or make the assumption explicit before drafting.

## Output Contract

Use these sections in order:

1. `EXECUTIVE SUMMARY` - 3-4 audience-tailored sentences.
2. `KEY METRICS` - clean table with available metrics.
3. `BOTTLENECK ANALYSIS`.
4. `CONVERSION ANALYSIS`.
5. `NOTABLE PATTERNS`.
6. `RECOMMENDED ACTIONS` - 2-4 actions, each tied to a data point.
7. `DATA QUALITY CALLOUTS` - always include.
8. `VALIDATION NOTE`.

## Metrics To Use When Available

- Total candidates in pipeline, this period and prior period.
- Active requisitions covered.
- Average time-in-stage by stage.
- Conversion rates between stages.
- New entries, exits, and rejections this period.
- Stalled candidates by stage and role.
- Longest-stuck candidate or anonymized candidate reference.
- Source/channel performance.
- Geography or seniority outliers.

## Audience Tone

- `DELIVERY MANAGER`: practical, role-specific, action-oriented.
- `HIRING MANAGER`: focused on the open req and decisions needed.
- `LEADERSHIP`: concise, strategic, risk-aware, no individual candidate names.
- `INTERNAL TEAM`: operational, detailed, candid, useful for process improvement.

## Data Rules

- Never fabricate numbers.
- Never estimate a missing metric unless the user explicitly asks for an estimate; label estimates clearly.
- Quote the data when making strong claims, such as `Per the input, 12 candidates spent more than 14 days in Awaiting Tech Screen`.
- Distinguish correlation from causation. Use `appears to coincide with`, not `caused by`, unless the data proves cause.
- Flag unusually positive results as well as bottlenecks.
- If prior-period data is absent, do not claim a trend.
- Always include `DATA QUALITY CALLOUTS`.

## Privacy Rules

- Never reference individual candidate names in leadership reports. Use `Candidate A in role X` or aggregate descriptions.
- Avoid unnecessary personal data in any report.
- For DM/HM reports, include candidate names only if the supplied data includes them and the audience is expected to act on individual candidates.

## Data Quality Callouts

Always check for:

- Missing stage, status, date, source, role, recruiter, or rejection reason fields.
- Candidates marked rejected with no rejection date.
- Candidates with impossible date sequences.
- Duplicate candidate rows.
- Stale statuses.
- Inconsistent stage naming.
- Any data gap that could change the conclusion.

## Example Prompts For Recruiters

```text
Use $pipeline-report-generator to create this week's pipeline report for a Delivery Manager. Focus on bottlenecks and recommended actions:
[paste pipeline export]
```

```text
Use $pipeline-report-generator to compare this month to last month for leadership. Do not mention candidate names:
[paste current period data]
[paste prior period data]
```

```text
Use $pipeline-report-generator to find the biggest time-in-stage outliers and data quality issues in this ATS export:
[paste CSV/table]
```

```text
Use $pipeline-report-generator to produce an internal recruiting operations report with conversion drops and source-channel patterns:
[paste data]
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It focuses on no fabricated numbers, audience tailoring, data citations, privacy handling, conversion and bottleneck analysis, and mandatory data quality callouts.
