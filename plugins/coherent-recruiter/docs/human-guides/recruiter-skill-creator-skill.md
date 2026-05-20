# Recruiter Skill Creator Skill

**Skill ID:** `$recruiter-skill-creator`

The Recruiter Skill Creator helps turn recruiter Custom GPTs, prompt files, eval kits, and workflow ideas into complete Codex skill packages. It follows the pattern used in this course workspace: an agent-facing skill folder, an eval checklist, a separate human-facing usage guide, workflow links to other recruiter skills, and a shareable zip package when useful.

This skill is useful when you want to keep building a library of recruiter skills without manually remembering the structure every time. It makes sure each new skill is not only technically usable by Codex, but also explainable to recruiters who need prompt examples, workflow ideas, and installation or sharing instructions.

## Prompt Examples

```text
Use $recruiter-skill-creator to convert these Custom GPT files into a Codex skill:
[paste or reference Custom GPT markdown]
[paste or reference eval kit markdown]

Also create the human usage guide with prompt examples and package it as a zip.
```

```text
Use $recruiter-skill-creator to create the next recruiter skill from this workflow idea:
Recruiters need a skill that turns hiring manager calibration notes into a shortlist review brief.
Create SKILL.md, a usage guide, and workflow connections to the existing recruiter skills.
```

```text
Use $recruiter-skill-creator to improve this existing skill. Add a separate markdown guide for recruiters with 3-5 prompts, workflow ideas, and sharing instructions:
[paste skill folder or file paths]
```

```text
Use $recruiter-skill-creator to package this skill for my recruiting team and tell me how they should install and invoke it:
[skill folder path]
```

```text
Use $recruiter-skill-creator to update the workflow docs after adding a new skill. Connect it to Boolean Builder, Outreach Library, Candidate FAQ Responder, Prescreen Call Transcriber, and Scorecard Writer where relevant.
```

## Workflow Ideas

Use it whenever a Custom GPT is ready to become a reusable Codex skill. Paste the Custom GPT prompt and eval kit, then ask for the skill folder, usage guide, and package.

Use it after a training session. If recruiters discover better prompts or missing workflow steps, ask this skill to update the relevant `*-skill.md` guide and the skill instructions.

Use it as a quality gate before sharing skills with a team. It can check metadata, remove scaffold placeholders, package the skill, and explain how colleagues should install it.

Use it to keep workflow documentation connected. When a new recruiter skill is added, it can update nearby usage guides so the team sees how skills fit together.

## Connections With Other Skills

**Skill Creator -> Recruiter Skill Creator:** use the system `$skill-creator` for general skill-building rules, then use `$recruiter-skill-creator` for the recruiter-specific packaging and human guide pattern.

**Recruiter Skill Creator -> All Recruiter Skills:** use this skill to create or revise `$jd-drafter`, `$recruiter-boolean-builder`, `$outreach-library`, `$candidate-faq-responder`, `$prescreen-call-transcriber`, `$scorecard-writer`, and related recruiter workflow skills.

**Custom GPT -> Recruiter Skill Creator -> Recruiter Team:** use a Custom GPT prompt and eval kit as source material, convert them into a Codex skill, then share the zip and usage guide with the recruiting team.

## Sharing With Recruiters

Share two files for each created skill:

1. `<skill-id>-skill.zip`
2. `<skill-id>-skill.md`

Recruiters can install the skill by unzipping the package into:

```text
~/.codex/skills/<skill-id>
```

Then they can invoke it with:

```text
Use $<skill-id> to ...
```

For a 17-person team, the better long-term approach is to keep all approved skill folders and usage guides in one shared internal repository or SharePoint folder. That gives the team one source of truth and makes updates easier than sending many zip files around.

## Distribution Notes

Zip packages are good for quick manual sharing through Teams, Slack, SharePoint, or email. A repository or controlled SharePoint folder is better for versioning, approvals, and ongoing maintenance.

Do not include confidential client data, real candidate data, sensitive compensation policies, or legal boilerplate in a broadly shared skill package unless it is approved for that audience.

## Possible Skill Improvements

Add a script that generates the usage-guide skeleton automatically from a skill ID and display name.

Add an approved repository layout for publishing the full recruiter skill library.

Add a release checklist for training sessions: what changed, which skill zip to share, which prompt examples to demo, and which evals to rerun.
