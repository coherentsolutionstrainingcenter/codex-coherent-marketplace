---
name: recruiter-skill-creator
description: Converts recruiter-focused Custom GPT prompts, eval kits, role workflows, and training notes into complete Codex skill packages. Use when creating or updating recruiter skills from Custom GPT markdown files, generating the agent-facing SKILL.md, moving evals into references/eval-checklist.md, creating a separate human-facing *-skill.md usage guide with prompt examples and workflow ideas, linking the new skill to existing recruiter skills, validating metadata, and packaging the skill for sharing with recruiting teams.
---

# Recruiter Skill Creator

## Overview

Create recruiter-focused Codex skills from Custom GPT source documents and this course workspace's established pattern. Produce both the agent-facing skill and the separate recruiter-facing usage documentation.

Do not modify the system `skill-creator` skill. This skill adds a domain layer for recruiter workflows, training, packaging, and human usage guides.

## Expected Inputs

Use any available source:

- Custom GPT prompt markdown, such as `05_jd_drafter.md`.
- Eval kit markdown, such as `eval_05_jd_drafter.md`.
- Existing recruiter skill folders or `*-skill.md` usage guides.
- User instructions from the current chat about naming, sharing, workflows, or team rollout.
- A rough idea for a new recruiter workflow when no Custom GPT file exists.

If only a rough idea is provided, ask for missing source material only when the skill would otherwise be unsafe or too vague. Prefer making a conservative first version when the workflow is clear.

## Output Artifacts

For each recruiter skill, create or update these artifacts:

1. `<skill-id>/SKILL.md` - agent-facing instructions only.
2. `<skill-id>/agents/openai.yaml` - UI metadata.
3. `<skill-id>/references/eval-checklist.md` - optional, created when an eval kit or regression checks exist.
4. `<skill-id>-skill.md` - human-facing usage guide outside the skill folder.
5. `<skill-id>-skill.zip` - shareable package when the user asks about sharing, distribution, or when the workspace already uses zip packages.

Keep user-facing docs outside the skill folder. The skill folder should contain only files that support agent execution.

## Creation Workflow

### 1. Inspect The Workspace

Read the source Custom GPT and eval markdown. Check existing skills with `rg --files` and inspect nearby `*-skill.md` files so naming, tone, workflow links, and package conventions stay consistent.

Prefer skill IDs that are short, hyphen-case, and action/domain specific, such as:

- `jd-drafter`
- `outreach-library`
- `candidate-faq-responder`
- `recruiter-boolean-builder`

### 2. Initialize The Skill

Use the system skill creator initializer when creating a new skill:

```text
init_skill.py <skill-id> --path . --resources references --interface display_name=... --interface short_description=... --interface default_prompt=...
```

Use `references` when there is an eval kit. Use scripts or assets only when the recruiter workflow needs deterministic automation or reusable templates.

### 3. Write SKILL.md

Make `SKILL.md` concise and operational. Include:

- YAML frontmatter with only `name` and `description`.
- Overview.
- Intake decision or workflow decision.
- Required inputs.
- Output contract.
- Non-negotiable safety, evidence, or policy rules.
- Tone rules.
- Example prompts for recruiters when useful.
- Validation reference pointing to `references/eval-checklist.md` when present.

Move long evals, templates, examples, or scoring rules into references. Do not paste training commentary or survey background into `SKILL.md` unless it changes agent behavior.

### 4. Convert Eval Kits

Convert eval markdown into `references/eval-checklist.md`.

Keep:

- Smoke tests.
- Regression checks.
- Expected behaviors.
- Scoring target.
- Critical failure modes.

Remove or condense long teaching notes unless they help future validation.

### 5. Create The Human Usage Guide

Create `<skill-id>-skill.md` outside the skill folder. It is for recruiters, trainers, and colleagues, not for the agent.

Read `references/usage-doc-template.md` when writing or revising a usage guide.

The usage guide must include:

- Skill title and skill ID.
- One or two short paragraphs explaining what the skill does for people.
- Three to five prompt examples.
- Workflow ideas.
- Connections with existing recruiter skills.
- Sharing or distribution notes when relevant.
- Possible skill improvements.

### 6. Link Workflows Across Skills

After creating a new skill, update related `*-skill.md` files when the connection is natural. Keep these edits small.

Common recruiter chain:

```text
$jd-drafter -> $recruiter-boolean-builder -> $outreach-library -> $candidate-faq-responder -> $prescreen-call-transcriber -> $scorecard-writer
```

Other useful links:

- `$cv-format-converter -> $candidate-relevance-ranker`
- `$candidate-relevance-ranker -> $prescreen-call-transcriber`
- `$scorecard-writer -> $candidate-faq-responder`
- `$job-request-gap-analyzer -> $jd-drafter` when both exist.

### 7. Package For Sharing

When packaging is requested or expected, create:

```text
<skill-id>-skill.zip
```

The zip should contain the skill folder itself, not only its contents:

```text
<skill-id>/
  SKILL.md
  agents/openai.yaml
  references/eval-checklist.md
```

Do not include the human usage guide inside the zip unless the user explicitly asks. The guide is usually shared beside the package.

### 8. Validate

Run the official validator when available:

```text
quick_validate.py <skill-id>
```

If it fails because `PyYAML` is unavailable, perform a local fallback validation:

- Parse SKILL.md frontmatter with Ruby `YAML` or another available YAML parser.
- Check `name` equals the folder name.
- Check the name is lowercase hyphen-case.
- Check `description` is present, under 1024 characters, and has no angle brackets.
- Check `agents/openai.yaml` has quoted `display_name`, `short_description`, and a `default_prompt` mentioning `$<skill-id>`.
- Search for scaffold leftovers from the initializer, especially placeholder sections or bracketed placeholder text.
- Inspect zip contents with `zipinfo -1` when a package is created.

## Human Usage Guide Standard

The usage guide should not explain implementation details or repeat the full skill. It should help a recruiter or trainer understand:

- What the skill is for.
- When to use it.
- What to paste into Codex.
- How it connects to the rest of the recruiter workflow.
- How to share it with colleagues.

Use practical language and realistic recruiter prompts. Avoid internal agent concepts unless they help the colleague install or invoke the skill.

## Distribution Guidance

For small recruiter teams, share:

- `<skill-id>-skill.zip`
- `<skill-id>-skill.md`

Installation target:

```text
~/.codex/skills/<skill-id>
```

For repeated rollout, recommend a shared internal repository or approved SharePoint folder where the team can version skill folders and usage guides.

Warn the user not to include confidential client names, real compensation policies, private templates, legal text, or sensitive examples in a broadly shared package unless approved for that audience.

## Final Response Checklist

At the end of the task, report:

- Skill folder created or updated.
- Human usage guide created or updated.
- Eval checklist created or updated.
- Zip package created, if applicable.
- Related usage docs updated, if applicable.
- Validation performed and any validator limitation.

Use clickable file links in final responses.
