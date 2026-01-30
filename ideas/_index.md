# Ideas Index

Last Updated: [Date]

## Active Ideas

| # | Name | Status | Priority | Last Updated |
|---|------|--------|----------|--------------|
| - | - | - | - | - |

## Status Legend
- 💡 Ideation - Just conceived
- 🔬 Researching - Gathering data
- ✅ Validated - Research complete
- 🚀 Pursuing - Actively developing
- ⏸️ Parked - On hold

## Next Session Goals
1. [ ] Generate first batch of ideas
2. [ ] Select top 3 for research
3. [ ] Complete market sizing for #1 priority
```

---

### Step 7: Restart Claude Desktop

1. Close Claude Desktop completely (check system tray, right-click Claude icon → Quit)
2. Reopen Claude Desktop
3. The MCP connection should now be active

---

### Step 8: Verify MCP is Working

In Claude Desktop, start a new conversation and type:
```
Can you read the files in my linkedin-hunter folder? 
Please list what you find in the founder-profile folder.
```

If MCP is working, Claude will read and list your files. If not, we'll troubleshoot.

---

## How to Use Your New System

### Starting Each Session

Open Claude Desktop and say:
```
Please read my CLAUDE.md file and the founder profile files, then give me 
a status update on where we are with the healthcare innovation project.
```

Claude will:
1. Read your master instructions
2. Read your profile
3. Check your ideas folder
4. Tell you current status
5. Ask what you want to do

### Example Session Flows

**Generating Ideas:**
```
You: Let's ideate. I want 5 healthcare startup concepts focused on 
     smart EMRs and clinical documentation. Search the web for current 
     pain points in India.

Claude: [Searches web, generates ideas, SAVES them to your folders]

You: Save these to my ideas folder, each in its own subfolder.

Claude: [Creates folders, saves concept.md files]
```

**Researching an Idea:**
```
You: Research idea #2 (voice-enabled EMR). I need market sizing for 
     India and UAE, and competitor analysis.

Claude: [Reads the concept file, searches web, creates research]

You: Save the research to that idea's folder.

Claude: [Saves market-research.md and competitors.md]
```

**Checking Status:**
```
You: Give me a status update on all ideas.

Claude: [Reads all folders, summarizes what exists, what's missing]
```

**Creating Documents:**
```
You: Create an investor pitch deck for the telemedicine concept using 
     all the research we've gathered.

Claude: [Reads all files for that idea, creates PowerPoint, saves it]
```

---

## Syncing to GitHub (Simple Method)

Since you have a GitHub repository, here's the easiest way to sync:

### Option A: GitHub Desktop (Recommended - No Command Line)

1. Download GitHub Desktop: **https://desktop.github.com/**
2. Install and sign in with your GitHub account
3. Click "Clone a repository"
4. Select `vikaslk/linkedin-hunter`
5. For local path, choose your `Documents/linkedin-hunter` folder
6. Now your local folder IS your GitHub repo

**To sync changes:**
1. Open GitHub Desktop
2. You'll see all changed files listed
3. Type a summary (e.g., "Added 3 new ideas")
4. Click "Commit to main"
5. Click "Push origin"

### Option B: Manual Upload (Simplest)

1. Go to github.com/vikaslk/linkedin-hunter
2. Navigate to the folder where you want to add a file
3. Click "Add file" → "Upload files"
4. Drag and drop from your local folder
5. Click "Commit changes"

---

## Troubleshooting

### "MCP not working" - Claude can't read files

**Check 1**: Is Node.js installed?
- Open Command Prompt
- Type `node --version`
- Should show a version number

**Check 2**: Is the config file correct?
- Go to `%APPDATA%\Claude`
- Open `claude_desktop_config.json`
- Make sure the path matches your actual folder
- Make sure you used `\\` (double backslashes) in paths

**Check 3**: Did you restart Claude Desktop?
- Must fully quit (not just minimize)
- Reopen the app

**Check 4**: Does the folder exist?
- Open File Explorer
- Navigate to the exact path in your config
- Make sure `linkedin-hunter` folder exists

### "Permission denied" errors

- Make sure the folder is in your Documents, not a protected location
- Don't use OneDrive folders (can cause permission issues)

---

## Quick Reference Card

### Trigger Phrases

| To Do This | Say This |
|------------|----------|
| Start a session | "Read CLAUDE.md and give me a status update" |
| Generate ideas | "Let's ideate on [topic]" |
| Research an idea | "Research [idea name]" |
| Assess funding | "Assess funding options for [idea]" |
| Build thesis | "Build investment thesis for [idea]" |
| Create deck | "Create pitch deck for [idea]" |
| LinkedIn prep | "Find LinkedIn prospects for [idea]" |
| Check status | "Status update" |
| Save something | "Save this to [folder/filename]" |

### Folder Quick Reference

| Content Type | Save To |
|--------------|---------|
| New idea concept | `/ideas/[idea-name]/concept.md` |
| Market research | `/ideas/[idea-name]/market-research.md` |
| Competitor analysis | `/ideas/[idea-name]/competitors.md` |
| Funding assessment | `/ideas/[idea-name]/funding.md` |
| Investment thesis | `/ideas/[idea-name]/thesis.md` |
| LinkedIn targets | `/ideas/[idea-name]/linkedin-targets.md` |
| Internal docs | `/documents/internal/` |
| Investor decks | `/documents/investor-ready/` |

---

## What To Do Right Now

### Checklist

- [ ] **Install Node.js** from https://nodejs.org (LTS version)
- [ ] **Verify Node.js**: Open Command Prompt, type `node --version`
- [ ] **Create config file**: Follow Step 3 above
- [ ] **Create folder structure**: Follow Step 4 above
- [ ] **Create CLAUDE.md**: Follow Step 5 above
- [ ] **Create _index.md**: Follow Step 6 above
- [ ] **Restart Claude Desktop**: Fully quit and reopen
- [ ] **Test MCP**: Ask Claude to read your files

### Your First Working Session

Once setup is complete, start Claude Desktop and paste this:
```
I'm Dr. Vikas, starting my healthcare innovation project.

Please:
1. Read the CLAUDE.md file in my linkedin-hunter folder
2. Read my founder profile files
3. Confirm you can access my file system
4. Then let's generate our first batch of 5 healthcare startup ideas 
   focused on:
   - Smart EMRs with voice/AI
   - Health data analytics
   - Metabolic health solutions

Search the web for current pain points in India and UAE before generating ideas.
Save each idea to its own folder under /ideas/