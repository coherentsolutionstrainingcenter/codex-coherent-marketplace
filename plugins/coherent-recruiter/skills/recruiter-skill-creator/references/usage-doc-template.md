# Recruiter Skill Usage Guide Template

Use this template when creating `<skill-id>-skill.md` files outside the skill folder.

## Structure

````markdown
# <Human Skill Name> Skill

**Skill ID:** `$<skill-id>`

<One short paragraph explaining what the skill does in recruiter language.>

<One short paragraph explaining what makes it useful, what it is careful about, or what input it needs.>

## Prompt Examples

```text
Use $<skill-id> to ...
[paste realistic recruiter input]
```

```text
Use $<skill-id> to ...
[paste realistic recruiter input]
```

```text
Use $<skill-id> to ...
[paste realistic recruiter input]
```

## Workflow Ideas

Use it ...

Use it ...

Use it ...

## Connections With Other Skills

**Skill A -> Skill B:** <one practical handoff sentence.>

**Skill B -> Skill C:** <one practical handoff sentence.>

**Workflow chain:** <show the likely recruiter workflow when helpful.>

## Sharing With Recruiters

Share `<skill-id>-skill.zip` plus this usage guide with colleagues.

Install by unzipping the package into:

```text
~/.codex/skills/<skill-id>
```

Invoke it with:

```text
Use $<skill-id> to ...
```

## Distribution Notes

Use Slack, Teams, SharePoint, email, or an internal repository depending on team size. Keep approved source material separate from confidential client or candidate data.

## Possible Skill Improvements

Add ...

Add ...
````

## Writing Rules

- Keep the first two paragraphs human-facing, not agent-facing.
- Use three to five prompt examples.
- Use realistic recruiter tasks and pasted-input placeholders.
- Mention workflow connections only when they are useful.
- Add sharing instructions when the user asks about team rollout or package distribution.
- Do not paste the full `SKILL.md` into the usage guide.
