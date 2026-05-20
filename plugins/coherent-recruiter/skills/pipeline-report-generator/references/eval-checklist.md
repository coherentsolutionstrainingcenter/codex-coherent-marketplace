# Pipeline Report Generator Eval Checklist

Use this reference only when validating or revising the skill. Do not load it for normal report generation unless the user asks to evaluate the skill.

## Smoke Tests

```text
Generate a weekly Delivery Manager report from a small pipeline table.
```

```text
Generate a leadership report from candidate-level data with names included.
```

```text
Compare current month data with no prior-period data supplied.
```

```text
Analyze a table with missing stage dates and rejected candidates without rejection dates.
```

```text
Generate a report where one stage has unusually fast conversion.
```

## Regression Checks

### Standard report

Expected:
- Includes all required sections.
- Executive summary matches the audience.
- Key metrics are in a table.
- Recommended actions tie to specific data points.
- Data quality callouts are present.

### No fabricated numbers

Expected:
- Uses `Not available in input data` for missing metrics.
- Does not invent trends without prior-period data.
- Does not calculate unsupported conversion rates.

### Data citation

Expected:
- Strong claims cite the input data.
- Bottleneck claims mention stage, count, or time-in-stage from the data.

### Correlation vs causation

Expected:
- Uses cautious language for possible causes.
- Does not claim why a drop happened unless the data supports it.

### Leadership privacy

Expected:
- Removes individual candidate names from leadership reports.
- Uses anonymized references or aggregates.

### Data quality

Expected:
- Flags missing values, inconsistent dates, duplicates, stale statuses, and rejected-without-date issues.
- Explains how data gaps may affect conclusions.

### Positive outliers

Expected:
- Flags unusually positive conversion or speed, not only problems.
- Suggests learning from positive outliers when appropriate.

## Scoring

A working v1 should never fabricate metrics, omit data quality callouts, expose candidate names in leadership reports, or treat correlation as proven causation.
