# Use The Coherent Marketplace In Codex

This guide is for people who want to use plugins from the Coherent Marketplace in their local Codex app.

## 1. Clone The Marketplace

Choose a stable folder for local Codex marketplaces:

```bash
mkdir -p ~/codex-marketplaces
git clone https://github.com/coherentsolutionstrainingcenter/codex-coherent-marketplace.git ~/codex-marketplaces/coherent-marketplace
```

This is a public repository, so no authentication is required.

## 2. Register The Marketplace In Codex

Open your Codex config file:

```bash
open ~/.codex/config.toml
```

If the file does not open, create it:

```bash
mkdir -p ~/.codex
touch ~/.codex/config.toml
open ~/.codex/config.toml
```

Add this block, using the absolute path where you cloned the repository:

```toml
[marketplaces.coherent]
source_type = "local"
source = "/Users/<you>/codex-marketplaces/coherent-marketplace"
```

The `source` value must point to the repository root, the folder that contains `.agents/plugins/marketplace.json`.

## 3. Enable The Recruiter Plugin

In the same `~/.codex/config.toml` file, add:

```toml
[plugins."coherent-recruiter@coherent"]
enabled = true
```

Save the file and restart Codex.

## 4. Confirm It Loaded

After restarting Codex, the plugin should appear as `Coherent Recruiter`.

You can test it in a new Codex conversation with prompts like:

```text
Use Coherent Recruiter to turn this hiring intake into missing questions and a draft JD.
```

```text
Use Coherent Recruiter to convert this CV into a client-ready recruiter profile.
```

```text
Use Coherent Recruiter to build Boolean sourcing strings for this role.
```

## 5. Update The Marketplace Later

When the repository owner publishes updates, pull the latest changes:

```bash
cd ~/codex-marketplaces/coherent-marketplace
git pull
```

Restart Codex after pulling updates.

## Troubleshooting

If the plugin does not appear, check these items:

1. `~/.codex/config.toml` has `[marketplaces.coherent]`.
2. The marketplace `source` path is absolute and points to the cloned repository root.
3. The cloned repository contains `.agents/plugins/marketplace.json`.
4. The plugin is enabled with `[plugins."coherent-recruiter@coherent"]`.
5. Codex was fully restarted after the config change.

If you already have a `[marketplaces.coherent]` block, update the existing block instead of adding a duplicate.
