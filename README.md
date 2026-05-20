# Coherent Marketplace

This repository is a Codex plugin marketplace for Coherent persona plugins. It is designed as a single holder for department-focused plugins that support internal courses, enablement materials, and practical workflows.

The first installable plugin is `coherent-recruiter`, displayed in Codex as `Coherent Recruiter`. Future department plugins are represented as placeholder folders until their full plugin packages are ready.

## Current Layout

```text
.agents/plugins/marketplace.json
plugins/coherent-recruiter/.codex-plugin/plugin.json
plugins/coherent-recruiter/skills/
plugins/coherent-recruiter/docs/
plugins/coherent-recruiter/assets/
plugins/coherent-hr/README.md
plugins/coherent-sales/README.md
plugins/coherent-marketing/README.md
plugins/coherent-delivery/README.md
plugins/coherent-project-management/README.md
plugins/coherent-business-analytics/README.md
```

The marketplace file is the entry point Codex reads. Only folders listed in `.agents/plugins/marketplace.json` are installable plugins. README-only folders are placeholders for future work.

## Naming

The marketplace uses:

- Marketplace ID: `coherent`
- Marketplace display name: `Coherent Marketplace`
- First plugin ID: `coherent-recruiter`
- First plugin display name: `Coherent Recruiter`

This keeps the user-facing names short while leaving the internal IDs stable and explicit.

## For The Repository Owner

Use [docs/publish-to-github.md](docs/publish-to-github.md) to turn this folder into a GitHub repository.

The short version is:

```bash
git init
git add .gitignore README.md docs .agents/plugins/marketplace.json plugins/coherent-*
git commit -m "Publish Coherent Codex plugin marketplace"
```

Then create an empty GitHub repository and push this folder to it.

## For Codex Users

For non-technical users, start with [PLUGINS-FOR-DUMMIES.md](PLUGINS-FOR-DUMMIES.md). It explains the ZIP download flow and the exact Codex config blocks to paste.

For recruiter workflow examples, use [plugins/coherent-recruiter/EXAMPLE-WORKFLOWS.md](plugins/coherent-recruiter/EXAMPLE-WORKFLOWS.md). It contains copy-paste prompts that combine multiple Coherent Recruiter skills.

Use [docs/use-this-marketplace.md](docs/use-this-marketplace.md) to clone the marketplace and enable the plugin in Codex.

The short version is:

```bash
git clone https://github.com/coherentsolutionstrainingcenter/codex-coherent-marketplace.git ~/codex-marketplaces/coherent-marketplace
```

Then add the marketplace path to `~/.codex/config.toml` and enable:

```toml
[marketplaces.coherent]
source_type = "local"
source = "/Users/<you>/codex-marketplaces/coherent-marketplace"

[plugins."coherent-recruiter@coherent"]
enabled = true
```

Restart Codex after editing the config. The plugin should appear as `Coherent Recruiter`.

## Adding More Plugins Later

When a future department plugin is ready, replace its placeholder folder with a complete plugin folder containing `.codex-plugin/plugin.json`, skills, docs, and assets. Then register it in `.agents/plugins/marketplace.json`.

Each marketplace entry should look like this:

```json
{
  "name": "coherent-sales",
  "source": {
    "source": "local",
    "path": "./plugins/coherent-sales"
  },
  "policy": {
    "installation": "AVAILABLE",
    "authentication": "ON_INSTALL"
  },
  "category": "Productivity"
}
```

Keep the `source.path` relative to the repository root so the marketplace works after other people clone it.
