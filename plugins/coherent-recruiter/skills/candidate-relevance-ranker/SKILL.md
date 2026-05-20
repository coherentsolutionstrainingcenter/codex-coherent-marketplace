---
name: candidate-relevance-ranker
description: Compares a job description or role brief against a batch of candidate CVs, LinkedIn snippets, or short bios and suggests a qualitative recruiter review order with evidence. Use for recruiter-led shortlisting support, not hiring decisions; refuses batches over 25 candidates; avoids numeric scores, protected characteristics, automated decision language, and unsupported fit claims.
---

# Candidate Relevance Ranker

## Overview

Analyze candidate profiles against a role brief and suggest an evidence-based review order for the recruiter. The output is a triage aid, not a decision, rejection, or automated ranking for final use.

This skill is high-risk in recruiting contexts. Keep human review, qualitative language, and evidence quotes visible in every output.

## Required Intake

The user should provide:

- Job description or role brief.
- Must-have and nice-to-have requirements, if available.
- Candidate profiles, CV excerpts, LinkedIn snippets, or short bios.

Refuse or ask the user to split the task if there are more than 25 candidates in one batch. If the JD is missing, ask for it before ranking. If must-haves are unclear, infer only from the supplied JD and flag uncertainty.

## Output Contract

For each candidate, use this exact structure:

```text
----- Candidate [N]: [Name, initials, or identifier] -----

EVIDENCE OF FIT:
- 2-4 specific items from the CV/profile that match must-have or nice-to-have requirements. Quote the source when possible.

EVIDENCE OF GAP:
- 2-4 specific items where the CV/profile does not clearly match the role. Quote the source when possible or state what is not shown.

UNCERTAINTY:
- Information the profile is silent on that matters for the role.

CONTEXT FLAG:
- Include only if a pattern warrants human review, such as career gaps, multiple short stints, possible AI-generated CV, missing recent experience, or inconsistent dates.

RECOMMENDATION FOR RECRUITER REVIEW:
- One of the approved qualitative phrases.

----- end candidate block -----
```

After all candidate blocks, include:

1. `SUGGESTED REVIEW ORDER` - candidates in the recommended order, with one-sentence evidence-based rationale each.
2. `WHAT THIS RANKING DOES NOT DO` - state that this is not a final ranking, not a hire/reject recommendation, not based on hidden attributes, and must be validated by the recruiter.

## Approved Recommendation Language

Use only these qualitative labels:

- `Strong evidence of fit - recommend recruiter review first`
- `Mixed evidence - worth a closer look`
- `Weak evidence based on this profile - recruiter to confirm if additional context exists`

Do not use numeric scores, percentages, star ratings, traffic-light ratings, or pass/fail labels.

## Evidence Rules

- Quote the CV/profile directly when claiming fit or gap.
- Do not infer experience that is not shown.
- Separate must-have evidence from nice-to-have evidence when useful.
- If a profile is silent on something important, put it in `UNCERTAINTY`, not `EVIDENCE OF GAP`, unless the absence itself is meaningful.
- Do not characterize culture fit, motivation, communication style, or attitude unless the source explicitly contains relevant evidence, and even then mark it for recruiter validation.

## Bias And Compliance Rules

- Never use protected characteristics: age, birth year, gender, nationality, ethnicity, religion, marital status, family status, disability, photo descriptions, or similar attributes.
- If protected attributes appear in the source, ignore them and add `[FILTERED: protected attributes present in source]`.
- Do not reference candidate names in the recommendation wording. Use `Candidate 1`, initials, or identifiers in recommendation summaries.
- Never make hire/reject decisions.
- Never say a recruiter should advance or reject solely based on the ranking.
- Under high-risk recruitment rules, the recruiter must independently review every candidate they intend to advance or reject.

## Quality Flags

Flag possible AI-generated or low-information CV patterns neutrally:

```text
[POSSIBLE AI-WRITTEN CV - recruiter validates with conversation]
```

Examples:

- Repeated identical phrasing across roles.
- Generic tools such as `modern frameworks` without names.
- Metrics without context.
- Missing dates or inconsistent timelines.
- Very polished claims with little project detail.

## Example Prompts For Recruiters

```text
Use $candidate-relevance-ranker to compare these 8 candidates against this Senior Java JD. Do not use numeric scores; give me a suggested review order with evidence.
[paste JD]
[paste candidate profiles]
```

```text
Use $candidate-relevance-ranker to re-order this shortlist with more weight on AWS and Kafka experience. Keep the output as recruiter review guidance, not a decision.
[paste JD and profiles]
```

```text
Use $candidate-relevance-ranker to identify which profiles are missing must-have evidence before I spend time opening full CVs:
[paste role brief]
[paste snippets]
```

```text
Use $candidate-relevance-ranker to flag profiles that look too generic or possibly AI-written while still comparing them to the role:
[paste JD]
[paste profiles]
```

## Validation Reference

When testing or revising this skill, read `references/eval-checklist.md`. It focuses on batch limits, no numeric scoring, evidence quoting, protected-attribute filtering, and human-in-the-loop language.
