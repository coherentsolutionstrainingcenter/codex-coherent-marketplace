# Coherent Marketplace Plugins For Beginners

This guide is for recruiters and other non-technical users. It explains how to install the Coherent Marketplace in Codex so you can use the Coherent Recruiter plugin.

You do not need to know Git, GitHub, or programming.

## What You Are Installing

You are installing one Codex plugin marketplace:

- Marketplace name: `Coherent Marketplace`
- Recruiter plugin name: `Coherent Recruiter`

The Coherent Recruiter plugin includes one recruiter persona plus specialist recruiter skills:

- Job description drafting
- CV/profile formatting
- Candidate review notes and suggested review order
- Boolean search strings
- Candidate outreach drafts
- Candidate FAQ and status reply drafts
- Follow-up message drafts
- Prescreen transcript and notes summaries
- Job request gap analysis
- Pipeline reports
- Rejection message drafts
- Interview scorecard drafts
- Recruiter skill creation support

Important: these tools create drafts and review aids. They do not make hiring decisions, automatically reject candidates, or send messages for you.

## Before You Start

You need:

- Codex installed on your computer
- Access to this GitHub repository:

```text
https://github.com/coherentsolutionstrainingcenter/codex-coherent-marketplace
```

This guide is for local Codex setup. It is not a browser extension and it is not installed inside the GitHub website.

## Step 1: Download The Marketplace

The easiest way is to download a ZIP file from GitHub.

1. Open this page:

```text
https://github.com/coherentsolutionstrainingcenter/codex-coherent-marketplace
```

2. Click the green `Code` button.
3. Click `Download ZIP`.
4. Open your `Downloads` folder.
5. Double-click the ZIP file to extract it.
6. You should now have a folder named something like:

```text
codex-coherent-marketplace-main
```

## Step 2: Move The Folder To A Stable Place

The folder must stay in one place. If you move it later, Codex will stop finding the plugin until the config is updated.

### On Mac

1. Open Finder.
2. Open your home folder. It usually has your name.
3. Create a folder named:

```text
codex-marketplaces
```

4. Move the extracted GitHub folder into `codex-marketplaces`.
5. Rename the extracted folder to:

```text
coherent-marketplace
```

At the end, the folder should be here:

```text
/Users/YourUsername/codex-marketplaces/coherent-marketplace
```

### On Windows

1. Open File Explorer.
2. Open your user folder. It is usually under `C:\Users\YourUsername`.
3. Create a folder named:

```text
codex-marketplaces
```

4. Move the extracted GitHub folder into `codex-marketplaces`.
5. Rename the extracted folder to:

```text
coherent-marketplace
```

At the end, the folder should be here:

```text
C:\Users\YourUsername\codex-marketplaces\coherent-marketplace
```

## Step 3: Add The Marketplace To Codex

Codex reads plugin settings from a file named `config.toml`.

The most reliable method is to paste a small command into Terminal or PowerShell. You do not need to understand the command; it creates the config entry for you.

If you already tried installing this marketplace before, ask your trainer before running the command again. Running it twice can create duplicate config blocks.

### Mac: Copy And Paste This Into Terminal

1. Open Terminal.
2. Copy and paste this whole block.
3. Press Enter.

```bash
mkdir -p "$HOME/.codex"
cat >> "$HOME/.codex/config.toml" <<EOF

[marketplaces.coherent]
source_type = "local"
source = "$HOME/codex-marketplaces/coherent-marketplace"

[plugins."coherent-recruiter@coherent"]
enabled = true
EOF
open "$HOME/.codex/config.toml"
```

The config file will open so you can quickly check it.

### Windows: Copy And Paste This Into PowerShell

1. Open PowerShell.
2. Copy and paste this whole block.
3. Press Enter.

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex" | Out-Null
$marketplacePath = ($env:USERPROFILE -replace '\\','/') + "/codex-marketplaces/coherent-marketplace"
@"

[marketplaces.coherent]
source_type = "local"
source = "$marketplacePath"

[plugins."coherent-recruiter@coherent"]
enabled = true
"@ | Add-Content "$env:USERPROFILE\.codex\config.toml"
notepad "$env:USERPROFILE\.codex\config.toml"
```

The config file will open so you can quickly check it.

## Step 4: Check The Config

Your config file should contain a block like this.

Mac example:

```toml
[marketplaces.coherent]
source_type = "local"
source = "/Users/sarah/codex-marketplaces/coherent-marketplace"

[plugins."coherent-recruiter@coherent"]
enabled = true
```

Windows example:

```toml
[marketplaces.coherent]
source_type = "local"
source = "C:/Users/sarah/codex-marketplaces/coherent-marketplace"

[plugins."coherent-recruiter@coherent"]
enabled = true
```

The exact username will be different on your computer.

If you already had a `[marketplaces.coherent]` or `[plugins."coherent-recruiter@coherent"]` block, do not add a second copy. Ask your trainer to help you keep only one copy of each block.

## Step 5: Restart Codex

Close Codex completely and open it again.

On Mac, use `Quit` from the app menu, then open Codex again. Closing only the window may not be enough.

## Step 6: Try The Plugin

Start a new Codex conversation and try one of these prompts:

```text
Use Coherent Recruiter to turn this hiring intake into missing questions and a draft JD.
```

```text
Use Coherent Recruiter to convert this CV into a client-ready recruiter profile.
```

```text
Use Coherent Recruiter to build Boolean sourcing strings for this role.
```

If Codex understands `Coherent Recruiter`, the setup worked.

## Troubleshooting

### I Do Not See Coherent Recruiter

Check these items:

1. Did you fully quit and reopen Codex?
2. Is the marketplace folder still named `coherent-marketplace`?
3. Is the folder inside `codex-marketplaces`?
4. Does your config file contain `[marketplaces.coherent]`?
5. Does your config file contain `[plugins."coherent-recruiter@coherent"]` with `enabled = true`?
6. Does the `source` path point to the folder that contains `.agents` and `plugins`?

### The Path Looks Wrong

The most common mistake is pointing Codex to the wrong folder.

Correct:

```text
.../codex-marketplaces/coherent-marketplace
```

Wrong:

```text
.../codex-marketplaces/coherent-marketplace-main
.../Downloads/codex-coherent-marketplace-main.zip
.../coherent-marketplace/plugins/coherent-recruiter
```

The path must point to the marketplace folder, not the ZIP file and not the individual recruiter plugin folder.

### The Config File Is Hard To Find

Ask your trainer or a technical colleague to check:

- The file location: `~/.codex/config.toml` on Mac
- The file location: `%USERPROFILE%\.codex\config.toml` on Windows
- The marketplace path inside the file
- The folder contains `.agents/plugins/marketplace.json`

## Updating Later

If your trainer says the plugin was updated, download the newest ZIP from GitHub again.

1. Go to:

```text
https://github.com/coherentsolutionstrainingcenter/codex-coherent-marketplace
```

2. Click `Code`.
3. Click `Download ZIP`.
4. Extract it.
5. Replace your old `coherent-marketplace` folder with the new one.
6. Restart Codex.

If you used Git instead of ZIP, update with:

```bash
cd ~/codex-marketplaces/coherent-marketplace
git pull
```

Then restart Codex.

## When Asking For Help

Send your trainer:

1. What step you reached.
2. A screenshot of your `config.toml` file.
3. A screenshot of your `codex-marketplaces` folder.
4. Any error message you saw.

## Extra Links

For technical users:

- [Coherent Recruiter example workflows](plugins/coherent-recruiter/EXAMPLE-WORKFLOWS.md)
- [Marketplace usage guide](docs/use-this-marketplace.md)
- [Publishing guide](docs/publish-to-github.md)
- [Repository README](README.md)
