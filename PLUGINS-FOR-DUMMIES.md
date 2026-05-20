# Coherent Marketplace Plugins For Dummies

**Don't know how to use GitHub or Git? No problem! This guide is for you.**

This guide explains how to download the Coherent Marketplace plugins and install them into Claude Code (Codex) so you can use AI-powered recruiting tools without technical knowledge.

---

## What You're Getting

The Coherent Marketplace provides **13 AI-powered recruiting skills** ready to use in Claude Code:

- **JD Drafter** — Write job descriptions from hiring requirements
- **CV Format Converter** — Convert CVs to recruiter-friendly profiles
- **Candidate Relevance Ranker** — Score candidates by fit to the role
- **Recruiter Boolean Builder** — Create advanced Boolean search strings
- **Outreach Library** — Generate personalized candidate outreach emails
- **Candidate FAQ Responder** — Answer candidate questions automatically
- **Follow-up Finder** — Generate follow-up messages for candidates
- **Prescreen Call Transcriber** — Transcribe and summarize candidate calls
- **Job Request Gap Analyzer** — Identify skill gaps between request and pool
- **Pipeline Report Generator** — Create recruitment pipeline reports
- **Rejection Letter Drafter** — Write professional rejection letters
- **Scorecard Writer** — Generate interview scorecards
- **Recruiter Skill Creator** — Build your own custom recruiting AI skills

---

## Step 1: Download The Marketplace (The Simple Way)

You don't need to understand Git. Just download the files as a ZIP.

### Option A: Using Your Browser (Easiest)

1. Open this link in your browser:
   ```
   https://github.com/coherentsolutionstrainingcenter/codex-coherent-marketplace
   ```

2. Look for the green **"Code"** button on the right side of the page.

3. Click it and select **"Download ZIP"**.

4. Wait for the download to complete. A file called `codex-coherent-marketplace-main.zip` will appear in your Downloads folder.

5. **Double-click the ZIP file** to extract it. On Mac, this happens automatically. On Windows, right-click and choose "Extract All".

6. Move the extracted folder to a stable location. We recommend:
   - **Mac**: `~/codex-marketplaces/coherent-marketplace`
   - **Windows**: `C:\Users\YourUsername\codex-marketplaces\coherent-marketplace`

   To do this:
   - Open Finder (Mac) or File Explorer (Windows)
   - Create a new folder called `codex-marketplaces` in your home directory if it doesn't exist
   - Drag the extracted `codex-coherent-marketplace-main` folder into it
   - Rename it to `coherent-marketplace` (remove the `-main` part)

### Option B: Using Git (If You're Comfortable)

If you know what Git is, use this command:

```bash
mkdir -p ~/codex-marketplaces
git clone https://github.com/coherentsolutionstrainingcenter/codex-coherent-marketplace.git ~/codex-marketplaces/coherent-marketplace
```

---

## Step 2: Find Your Codex Config File

Codex stores settings in a file called `config.toml`. You need to edit this file to tell Codex where to find the marketplace.

### On Mac:

1. Open **Finder** (the folder icon in your dock)
2. Press **Command + Shift + Period** (.) to show hidden files
3. Look for a folder called `.codex` (it starts with a dot)
4. If you don't see it, you need to create it:
   - Right-click in Finder
   - Select "New Folder"
   - Name it `.codex`
5. Inside the `.codex` folder, look for a file called `config.toml`
6. If it doesn't exist, create it:
   - Right-click in the folder
   - Select "New File"
   - Name it `config.toml`

### On Windows:

1. Open **File Explorer**
2. In the address bar at the top, type: `%USERPROFILE%`
3. Look for a folder called `.codex`
4. If you don't see it, create it:
   - Right-click in empty space
   - Select "New" → "Folder"
   - Name it `.codex`
5. Inside the `.codex` folder, look for `config.toml`
6. If it doesn't exist, create it:
   - Right-click in the folder
   - Select "New" → "Text Document"
   - Name it `config.toml` (make sure it ends in `.toml`, not `.txt`)

---

## Step 3: Edit The Config File

Now you need to tell Codex where to find the marketplace.

1. **Open** `config.toml` with a text editor:
   - **Mac**: Right-click the file, select "Open With", and choose a text editor (like TextEdit)
   - **Windows**: Right-click the file, select "Open With", and choose Notepad

2. **Copy and paste this into the file:**

   ```toml
   [marketplaces.coherent]
   source_type = "local"
   source = "/Users/YourUsername/codex-marketplaces/coherent-marketplace"
   
   [plugins."coherent-recruiter@coherent"]
   enabled = true
   ```

3. **Important**: Replace `YourUsername` with your actual username:
   - **Mac**: Open Terminal (Applications > Utilities > Terminal) and type `whoami` to see your username
   - **Windows**: Your username is usually shown at the start of paths in File Explorer

4. **Example** (if your username is "sarah"):
   ```toml
   [marketplaces.coherent]
   source_type = "local"
   source = "/Users/sarah/codex-marketplaces/coherent-marketplace"
   
   [plugins."coherent-recruiter@coherent"]
   enabled = true
   ```

5. **Save the file** (Command+S on Mac, Ctrl+S on Windows)

---

## Step 4: Restart Claude Code

Close Claude Code completely and reopen it.

- **Desktop App**: Quit the app and click the icon again to reopen
- **Web App**: Close the browser tab and reload
- **VS Code Extension**: Reload the VS Code window

---

## Step 5: Confirm It Worked

After restarting, you should see **"Coherent Recruiter"** available in Claude Code.

Try one of these prompts in a new Codex conversation:

```
Use Coherent Recruiter to turn this hiring intake into missing questions and a draft JD.
```

```
Use Coherent Recruiter to convert this CV into a client-ready recruiter profile.
```

```
Use Coherent Recruiter to build Boolean sourcing strings for this role.
```

If the plugin appears and responds, you're done! 🎉

---

## Troubleshooting: What If It Doesn't Work?

### The plugin doesn't appear in Codex

1. **Did you restart Codex?** Close it completely and reopen it.

2. **Is the path correct?** Open your `config.toml` file again and check:
   - Does it point to where you actually put the marketplace folder?
   - Is the path spelled correctly?
   - On Mac, does it start with `/Users/`? On Windows, does it start with `C:\Users\`?

3. **Is the file named correctly?** Make sure it's called `config.toml` (not `config.txt` or anything else).

4. **Do you have `[marketplaces.coherent]`?** Check that this section exists in your config file.

5. **Is the plugin enabled?** Check that you have `[plugins."coherent-recruiter@coherent"]` with `enabled = true` in your config file.

### Still stuck?

Ask your trainer or a technical person to help you check:
- The path in your `config.toml` file
- That the marketplace folder contains `.agents/plugins/marketplace.json`
- That the folder is in the location you specified in the config

---

## Updating Later

When the trainer provides updates to the plugins, you have two options:

### Option A: Download Again (Easiest)

1. Go back to the GitHub page: https://github.com/coherentsolutionstrainingcenter/codex-coherent-marketplace
2. Download the new ZIP file
3. Extract it and replace your `coherent-marketplace` folder
4. Restart Codex

### Option B: Using Git

If you used Git to download, you can update with one command:

```bash
cd ~/codex-marketplaces/coherent-marketplace
git pull
```

Then restart Codex.

---

## Questions or Issues?

Contact your trainer with:

1. What were you trying to do?
2. What happened? (include any error messages)
3. What have you already tried?

This helps them help you faster.

---

## Want to Learn More?

- **For Trainers and Technical People**: See [docs/use-this-marketplace.md](docs/use-this-marketplace.md) and [docs/publish-to-github.md](docs/publish-to-github.md)
- **To See What's Inside**: Check the [README.md](README.md)

---

**Happy recruiting with AI!** 🚀
