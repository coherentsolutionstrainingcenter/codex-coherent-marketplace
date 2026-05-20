# Pipeline Report Generator Skill

**Skill ID:** `$pipeline-report-generator`

The Pipeline Report Generator turns ATS exports, CSV or Excel tables, or pasted pipeline data into audience-specific recruiting reports. It highlights bottlenecks, conversion drops, time-in-stage outliers, data quality problems, and recommended actions.

This skill is accuracy-first. It should never invent metrics or trends. If the input does not contain a number, the report should say so.

## Prompt Examples

```text
Use $pipeline-report-generator to create this week's pipeline report for a Delivery Manager. Focus on bottlenecks and actions:
[paste pipeline export]
```

```text
Use $pipeline-report-generator to compare this month to last month for leadership. Do not mention candidate names:
[paste current period data]
[paste prior period data]
```

```text
Use $pipeline-report-generator to find time-in-stage outliers and data quality issues in this ATS export:
[paste CSV/table]
```

```text
Use $pipeline-report-generator to produce an internal recruiting operations report with conversion drops and source-channel patterns:
[paste data]
```

## Workflow Ideas

Use it weekly for Delivery Manager updates on open roles.

Use it monthly for leadership summaries where privacy and strategic risk framing matter.

Use it internally to find stale stages, missing data, and process inconsistencies before they become visible in stakeholder reports.

## Connections With Other Skills

**Follow-Up Finder -> Pipeline Report Generator:** stale candidate conversations found by `$follow-up-finder` can be reported as pipeline risks.

**Job Request Gap Analyzer -> Pipeline Report Generator:** repeated JR gaps can explain sourcing delays and become intake-quality metrics.

**Candidate Relevance Ranker -> Pipeline Report Generator:** ranking and screening patterns can become early funnel signals, if tracked carefully and without automated decision language.

Future useful companion skills: ATS export cleaner, Power BI narrative writer, weekly stakeholder brief generator, and data-quality audit assistant.
