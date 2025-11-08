# Setup Guide: Getting Started

**Time Required**: 30-45 minutes (one-time setup)

This guide walks you through installing and using the agentic research workflow.

---

## Prerequisites

Before starting, make sure you have:

### Required
- [ ] **Claude Access** - Claude AI or Claude Code (https://claude.ai)
- [ ] **GitHub Account** - Free account at https://github.com
- [ ] **Git Installed** - Download from https://git-scm.com
- [ ] **Google Account** - For Google Drive Desktop

### Recommended
- [ ] **Google Drive Desktop** - For syncing session notes (https://www.google.com/drive/download/)
- [ ] **VSCode or IDE** - For local development (https://code.visualstudio.com)
- [ ] **Terminal/Command Line** - Familiarity with basic git commands

---

## Step 1: Install Claude Skill (5 minutes)

The research automation Claude Skill is included in this repo.

### Copy the Skill to Claude

1. **Locate the skill files**
   - In this repo: `/claude-skill/research-project-init_v1/`
   - Files you need:
     - `Skill.md` (main skill definition)
     - `references/` (research guidance)
     - `assets/` (templates)

2. **Install in Claude**
   - Open Claude (or Claude Code)
   - Go to Settings → Skills or Custom Tools
   - Add new skill from `/Skill.md`
   - Name: "research-project-init"

3. **Test the skill**
   - Ask Claude: "Research a SaaS tool for managing team tasks"
   - If it asks clarifying questions, skill is working!

**Note**: If you have issues installing, see Troubleshooting section below.

---

## Step 2: Setup GitHub (10 minutes)

### Create a Test Repository

This gets you familiar with the workflow before starting a real project.

1. **Create GitHub repo from template**
   ```bash
   # Option A: Using GitHub CLI
   gh repo create my-first-project --template {template-repo-url}

   # Option B: Manual
   # 1. Find the agentic-research-workflow template repo
   # 2. Click "Use this template" → "Create a new repository"
   # 3. Name it: my-first-project
   # 4. Make it public (easier for friends to see)
   ```

2. **Clone to your computer**
   ```bash
   git clone https://github.com/{your-username}/my-first-project
   cd my-first-project
   ```

3. **Verify the structure**
   ```bash
   ls -la
   # You should see:
   # - CLAUDE.md
   # - tasks.md
   # - docs/
   # - session-notes/
   # - src/
   # - tests/
   # etc.
   ```

### Update Project Context

1. **Edit CLAUDE.md**
   ```bash
   # Open in your editor
   code CLAUDE.md
   ```

2. **Update placeholders**
   ```
   # [Project Name] → # My First Project
   GitHub: owner/repo-handle → GitHub: {your-username}/my-first-project
   Owner: [Name] → Owner: {Your Name}
   Status: [Research | In Development] → Status: In Development
   Last Updated: YYYY-MM-DD → Last Updated: 2025-11-06
   ```

3. **Commit the change**
   ```bash
   git add CLAUDE.md
   git commit -m "docs: Update CLAUDE.md project context"
   git push origin main
   ```

---

## Step 3: Setup Google Drive (5 minutes)

For automatic syncing of session notes (optional but recommended).

1. **Install Google Drive Desktop**
   - Download: https://www.google.com/drive/download/
   - Install and sign in with your Google account

2. **Enable sync for your projects folder**
   - Open Google Drive
   - Find (or create): `My Drive / AI_Projects`
   - Right-click → "Sync to this computer"
   - Creates local path: `G:\My Drive\AI_Projects\` (Windows) or `~/Drive/AI_Projects` (Mac/Linux)

3. **Verify sync**
   ```bash
   # Check the local path
   ls "G:\My Drive\AI_Projects"  # Windows
   ls ~/Drive/AI_Projects        # Mac/Linux
   ```

**Why**: Session notes sync automatically, so manager can review on phone without special tools.

---

## Step 4: Run Your First Workflow (15 minutes)

Now let's go through the complete workflow with your test project.

### 4a: Research Phase (10 minutes)

1. **Open Claude**
   - Go to https://claude.ai or open Claude Code
   - Start new conversation

2. **Trigger research skill**
   ```
   Research a project management SaaS tool for distributed teams
   ```

3. **Answer clarifying questions**
   - AI asks 5 questions about scope, market, etc.
   - Respond with answers (A/B/C/D format)

4. **Get research output**
   - 7 documents generated
   - Saved to: `G:\My Drive\AI_Projects\My_First_Project\docs\`
   - (Or you'll need to copy them manually)

### 4b: Setup Research in GitHub (3 minutes)

1. **Copy research documents**
   ```bash
   # From Google Drive docs folder to GitHub docs folder
   cp "G:\My Drive\AI_Projects\My_First_Project\docs\*" docs/
   ```

   Or: Manually copy files from Drive to `{repo}/docs/`

2. **Commit research**
   ```bash
   git add docs/
   git commit -m "docs: Add research documents from research-project-init skill"
   git push origin main
   ```

### 4c: Create PRD (Optional - just review)

1. **Open the PRD template**
   ```bash
   cat tasks/create-prd.md
   ```

2. **Use in Claude**
   - Copy content of `create-prd.md`
   - Paste into Claude
   - Follow the prompts
   - Generates PRD

3. **Save PRD**
   ```bash
   # Save as docs/PRD_project-management.md
   git add docs/PRD_*.md
   git commit -m "docs: Add PRD"
   git push
   ```

### 4d: Review the Complete Workflow

1. **Read full documentation**
   ```bash
   cat ../agentic-workflow-v2.md
   ```

2. **Understand each phase**
   - Research (automated)
   - Planning (PRD generation)
   - Tasks (task generation)
   - Development (session-based)
   - Approval (manager feedback)

---

## How to Use for Real Projects

Once you understand the workflow, use it for your actual project:

1. **Create new GitHub repo**
   ```bash
   gh repo create my-awesome-saas --template {your-template-url}
   ```

2. **Run research skill**
   - "Research [your actual idea]"
   - Get 7 research documents

3. **Copy to GitHub**
   - `cp research/* docs/`
   - `git add docs/ && git commit && git push`

4. **Create PRD**
   - Use `tasks/create-prd.md` template
   - Get manager approval

5. **Generate tasks**
   - Use `tasks/generate-tasks.md` template
   - Get manager approval

6. **Start development sessions**
   - Read CLAUDE.md and tasks.md
   - Work on sub-tasks
   - Create session notes
   - Manager approves
   - Continue

---

## File Locations Reference

### In This Repository

```
agentic-research-workflow/
├── README.md                           # Start here (you just read this!)
├── docs/
│   ├── agentic-workflow-v2.md         # Complete workflow (10,000 words)
│   ├── setup-guide.md                 # This file
│   └── CREDITS.md                     # Credits and attribution
├── claude-skill/
│   └── research-project-init_v1/
│       ├── Skill.md                   # Claude Skill definition
│       ├── references/
│       │   ├── research_prompts.md   # Research guidance
│       │   └── document_templates.md # Output templates
│       └── assets/
│           └── CLAUDE_template.md    # CLAUDE.md template
├── github-template/                    # Your project template
│   ├── README.md                      # Project README template
│   ├── CLAUDE.md                      # AI context file
│   ├── tasks.md                       # Task list template
│   ├── .gitignore
│   ├── requirements.txt
│   ├── docs/                          # For research docs
│   ├── session-notes/
│   │   ├── README.md                 # Session workflow
│   │   ├── _TEMPLATE.md              # Session template
│   │   └── (session logs go here)
│   ├── tasks/
│   │   ├── create-prd.md             # PRD generation prompt
│   │   └── generate-tasks.md         # Task generation prompt
│   ├── src/                           # Your source code
│   └── tests/                         # Your tests
└── examples/
    └── web-saas-example.md           # Example walkthrough
```

### In Your Projects (Google Drive)

```
G:\My Drive\AI_Projects\{ProjectName}\
├── docs/                              # Research docs (from skill)
│   ├── 00_PROJECT_OVERVIEW.md
│   ├── 01_Research_Brief.md
│   ├── 02_Market_Landscape.md
│   ├── 03_Technical_Feasibility.md
│   ├── 04_Go_To_Market.md
│   ├── 05_Risk_Assessment.md
│   ├── plan.md
│   └── PRD_*.md                       # (PRDs you create)
└── session-notes/                      # Synced from GitHub
    ├── YYYY-MM-DD-HHmm.md
    └── (manager edits approval here)
```

### In Your Projects (GitHub)

```
{github-repo}/
├── CLAUDE.md                          # AI context (customized)
├── tasks.md                           # Task list (customized)
├── README.md                          # Project README
├── docs/                              # Research + planning
│   ├── 00_PROJECT_OVERVIEW.md
│   ├── (all research docs)
│   └── PRD_*.md                       # PRDs you create
├── session-notes/                     # Development logs
│   ├── _TEMPLATE.md
│   └── YYYY-MM-DD-HHmm.md
├── tasks/                             # Task generation
│   ├── create-prd.md
│   └── generate-tasks.md
├── src/                               # Your code
└── tests/                             # Your tests
```

---

## Common Tasks

### Start a Development Session

```bash
# Read in this order
1. CLAUDE.md           (5 min - project context)
2. tasks.md            (5 min - what to work on)
3. Last session notes  (5 min - what was approved)

# Then work on next task in session-notes/YYYY-MM-DD-HHmm.md

git add session-notes/
git commit -m "session: Work on task 1.1"
git push
```

### Review Session Work (Manager)

1. Open Google Drive mobile app
2. Navigate to: `AI_Projects/{ProjectName}/session-notes/`
3. Open latest file
4. Read MANAGER SUMMARY section
5. Edit MANAGER APPROVAL section:
   - Status: APPROVED / CHANGES NEEDED / ROLLBACK / PAUSED
   - Date Reviewed: today's date
   - Response: feedback message
6. Save (syncs automatically)

### View Full Workflow Documentation

```bash
# Complete reference guide
cat docs/agentic-workflow-v2.md

# Or read in Claude
# Paste content into Claude and ask for summary
```

---

## Troubleshooting

### Issue: Claude Skill Not Working

**Symptom**: "I don't see the research-project-init skill"

**Solution**:
1. Check you copied all files:
   - Skill.md
   - references/ folder
   - assets/ folder
2. Verify file paths in Skill.md are correct
3. Ask Claude directly:
   - "Help me troubleshoot a Claude Skill installation"
   - Paste Skill.md content
4. If still issues, see `/claude-skill/README.md`

---

### Issue: Google Drive Sync Not Working

**Symptom**: "Files aren't syncing between GitHub and Drive"

**Solution**:
1. Check Google Drive Desktop is running
2. Verify sync folder is enabled:
   - Open Google Drive
   - Check `My Drive / AI_Projects` is synced
3. Wait 1-2 minutes for sync
4. Manually copy if needed:
   ```bash
   cp {repo}/session-notes/* "G:\My Drive\AI_Projects\{Project}\session-notes\"
   ```

---

### Issue: Git Push Failed

**Symptom**: "fatal: 'origin' does not appear to be a git repository"

**Solution**:
1. Check you cloned the repo:
   ```bash
   git remote -v
   ```
   Should show origin URL
2. If not, navigate to repo folder:
   ```bash
   cd {repo-folder}
   git remote add origin https://github.com/{your-username}/{repo-name}
   ```
3. Try push again:
   ```bash
   git push -u origin main
   ```

---

### Issue: Merge Conflict

**Symptom**: Git tells you there's a merge conflict

**Solution**:
1. Most common cause: Manager edited same session file
2. Check what changed:
   ```bash
   git status
   ```
3. If it's just MANAGER APPROVAL section:
   - Keep both changes (yours + manager's)
   - Edit file to merge
4. If complex conflict:
   ```bash
   git merge --abort  # Start over
   git pull           # Get latest
   ```

---

### Issue: "I don't understand the workflow"

**Solution**:
1. Read `/docs/agentic-workflow-v2.md` - complete reference
2. Check `/examples/web-saas-example.md` - concrete walkthrough
3. Ask Claude to explain:
   - Paste content into Claude
   - Ask: "Explain this workflow"
   - Ask specific questions: "How does phase 5 work?"

---

### Issue: "GitHub template repo not showing"

**Symptom**: Can't find the template on GitHub

**Solution**:
1. Go to: Your template repository URL (from setup guide or friend's repo)
2. Should see a "Use this template" button
3. If not:
   - Repo may not be public yet
   - Try cloning instead: `git clone {your-template-url} my-project`

---

## Next Steps

### After Setup Complete

1. **Read full documentation**
   - Start with: [agentic-workflow-v2.md](agentic-workflow-v2.md)
   - Time: 30-45 minutes

2. **See example workflow**
   - Read: [examples/web-saas-example.md](../examples/web-saas-example.md)
   - Time: 15-20 minutes

3. **Start your first project**
   - Use the workflow with your idea
   - Follow the 5 phases
   - Keep notes of what works/what doesn't

4. **Share with friends**
   - Send them your fork of this repository (or the original template)
   - They can repeat your setup

---

## Getting Help

### If Something Breaks

1. **Read troubleshooting above** (covers 90% of issues)
2. **Check the docs**
   - agentic-workflow-v2.md (complete reference)
   - specific READMEs in each folder
3. **Ask Claude**
   - Upload this entire repo to Claude
   - Describe your issue
   - Claude can help troubleshoot

### If You Find Bugs

1. Create an issue on GitHub
2. Or ask Claude to help debug
3. We'll improve the workflow based on feedback

---

## Quick Reference Commands

```bash
# Create new project from template
gh repo create {project-name} --template {your-template-url}

# Clone existing project
git clone https://github.com/{your-username}/{project-name}

# Check git status
git status

# Commit changes
git add .
git commit -m "description"

# Push to GitHub
git push origin main

# Pull latest changes
git pull origin main

# See git history
git log --oneline

# Check project structure
tree -L 2
# or
ls -la
```

---

## Support

- **Documentation**: See `/docs/` folder
- **Examples**: See `/examples/` folder
- **Claude Help**: Upload repo and ask Claude
- **GitHub Issues**: Create issue on repository

---

**Last Updated**: November 2025
**Setup Time**: 30-45 minutes
**Next Reading**: [agentic-workflow-v2.md](agentic-workflow-v2.md)
