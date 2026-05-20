# Candidate Relevance Ranker Skill

**Skill ID:** `$candidate-relevance-ranker`

The Candidate Relevance Ranker compares a role brief against a batch of candidate profiles and suggests the order in which a recruiter should review them. It uses evidence of fit, evidence of gaps, uncertainty, and quality flags; it does not make hire/reject decisions.

This skill is intentionally qualitative. It should not produce numeric scores, percentages, pass/fail labels, or automated decision language.

## Prompt Examples

```text
Use $candidate-relevance-ranker to compare these candidates against this Senior Java role. Give me a suggested review order with evidence, not scores.
[paste JD]
[paste candidate profiles]
```

```text
Use $candidate-relevance-ranker to re-rank this shortlist with more weight on AWS, Kafka, and fintech experience:
[paste JD]
[paste profiles]
```

```text
Use $candidate-relevance-ranker to show which candidates are missing must-have evidence before I open the full CVs:
[paste role brief]
[paste profile snippets]
```

```text
Use $candidate-relevance-ranker to compare these candidates and flag profiles that may be AI-written or too generic:
[paste JD]
[paste CV excerpts]
```

```text
Use $candidate-relevance-ranker to explain why Candidate 2 should or should not be reviewed before Candidate 5. Keep it evidence-based and non-decisive.
[paste JD and two profiles]
```

## Workflow Ideas

Use it after applications arrive in a batch. The output gives the recruiter a review order so they can inspect likely-relevant profiles first.

Use it after sourcing to compare LinkedIn snippets before deciding which profiles deserve deeper review.

Use it during calibration with a hiring manager: show evidence and uncertainty, then adjust must-haves or nice-to-haves.

## Connections With Other Skills

**JD Drafter -> Candidate Relevance Ranker:** use `$jd-drafter` to turn rough intake notes into a cleaner JD or role brief, then use this skill to compare candidate profiles against the validated requirements.

**Boolean Builder -> Candidate Relevance Ranker:** use `$recruiter-boolean-builder` to source candidates, then use this skill to triage the resulting profiles.

**CV Format Converter -> Candidate Relevance Ranker:** standardized CVs from `$cv-format-converter` make batch comparison easier and more consistent.

**Candidate Relevance Ranker -> Scorecard Writer:** after a candidate is interviewed, use `$scorecard-writer` to turn interview notes into evidence-based feedback rather than relying on CV relevance alone.

Future useful companion skills: ATS batch exporter, shortlist calibration report, hiring-manager summary writer, and audit note generator.
