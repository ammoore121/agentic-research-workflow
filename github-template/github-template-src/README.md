# Project Template

This is a template GitHub repository for AI-assisted development with research, planning, and session management.

## Quick Start

1. **Create new GitHub repo** from this template
2. **Clone to local machine**
3. **Copy research docs** from Google Drive to `docs/` folder
4. **Initial commit** with research documents
5. **Begin development** sessions using the workflow below

---

## What This Template Includes

### 📋 Planning & Research
- `docs/` - Research documents from [research-project-init skill](../Workflow_References/_Skills/research-project-init_v1/)
- `tasks/create-prd.md` - Prompt for creating Product Requirements Documents
- `tasks/generate-tasks.md` - Prompt for breaking PRDs into implementation tasks
- `tasks.md` - Active task list with hierarchical numbering (from [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks))

### 👨‍💻 Development
- `CLAUDE.md` - AI agent context (read on every session)
- `session-notes/` - Development session logs with manager approval workflow
- `src/` - Source code directory
- `tests/` - Test directory
- `requirements.txt` - Python dependencies

### 🔗 Workflows
- **Research Phase**: [docs/README.md](docs/README.md) - How research flows into code
- **Planning Phase**: [tasks/create-prd.md](tasks/create-prd.md) - PRD generation from research
- **Task Generation**: [tasks/generate-tasks.md](tasks/generate-tasks.md) - Breaking PRDs into tasks
- **Development Phase**: [session-notes/README.md](session-notes/README.md) - Session-based development with manager approval
- **Approval Flow**: [session-notes/README.md](session-notes/README.md) - How manager approval works

---

## Workflow: Research → Planning → Development

### Phase 1: Research (Google Drive)

**Tool**: [research-project-init Claude Skill](../Workflow_References/_Skills/research-project-init_v1/)

**Input**: Business idea or feature description

**Process**:
1. AI asks 5 clarifying questions
2. Conducts competitive analysis, market research, technical assessment
3. Generates comprehensive research documents

**Output** (saved to Google Drive):
```
G:\My Drive\AI_Projects\{ProjectName}\docs\
├── 00_PROJECT_OVERVIEW.md
├── 01_Research_Brief.md
├── 02_Market_Landscape.md
├── 03_Technical_Feasibility.md
├── 04_Go_To_Market.md
├── 05_Risk_Assessment.md
└── plan.md
```

**Time**: 30-60 minutes

---

### Phase 2: Setup GitHub Repo (~5 min manual work)

1. **Create** new GitHub repo from this template
   ```bash
   gh repo create {project-name} --template snarktank/project-template
   ```

2. **Clone** to local machine
   ```bash
   git clone https://github.com/{owner}/{project-name}
   cd {project-name}
   ```

3. **Copy research docs** from Drive to `docs/`
   ```bash
   # Copy from: G:\My Drive\AI_Projects\{ProjectName}\docs\
   # Paste into: {local-repo}\docs\
   ```

4. **Commit research**
   ```bash
   git add docs/
   git commit -m "docs: Add research documents from research-project-init skill"
   git push origin main
   ```

5. **Update CLAUDE.md**
   - Replace `[Project Name]` with actual project name
   - Update `GitHub:` with repo URL
   - Update `Owner:` with your name
   - Update strategic docs links to point to research

6. **Update README.md**
   - Describe the project briefly
   - Add any project-specific setup instructions

---

### Phase 3: Create PRD (~2-4 hours)

**Tool**: [tasks/create-prd.md](tasks/create-prd.md) prompt template

**Process**:
1. Review research documents
2. Ask 5 clarifying questions (A/B/C/D format)
3. Generate PRD with 13 sections:
   - Overview, Goals, User Stories, Functional Requirements, Non-Goals
   - Design Considerations, Technical Considerations, Success Metrics, Open Questions
   - Research Sources, Session Plan, Approval Status, Manager Notes

4. Get manager approval

**Output**: `docs/PRD_{feature-name}.md`

**Manager Decision**: ✅ Approved → Proceed to Phase 4

---

### Phase 4: Generate Tasks (~1-2 hours)

**Tool**: [tasks/generate-tasks.md](tasks/generate-tasks.md) prompt template

**Process**:
1. Create parent tasks from PRD (1.0, 2.0, 3.0)
2. Get manager approval on parent tasks
3. Break into detailed sub-tasks (1.1, 1.2, 1.3, etc.)
4. Add acceptance criteria to each task
5. Estimate time per task

**Output**: `tasks.md` with full task list

**Manager Decision**: ✅ Approved → Proceed to Phase 5

---

### Phase 5: Development Sessions

**Workflow**: [session-notes/README.md](session-notes/README.md)

**Session Cycle**:

```
┌─────────────────────────┐
│ SESSION START           │
│ AI reads:               │
│ - CLAUDE.md             │
│ - tasks.md              │
│ - Last approval         │
└──────────┬──────────────┘
           │
           ▼
┌─────────────────────────┐
│ WORK (1-2 hours)        │
│ - Implement task(s)     │
│ - Write tests           │
│ - Commit code           │
└──────────┬──────────────┘
           │
           ▼
┌─────────────────────────┐
│ SESSION END             │
│ AI creates note with:   │
│ - MANAGER APPROVAL      │
│ - MANAGER SUMMARY       │
│ - DETAILED NOTES        │
│ Push to GitHub          │
└──────────┬──────────────┘
           │
           ▼
┌──────────────────────────────┐
│ GOOGLE DRIVE SYNC            │
│ session-notes/ syncs to      │
│ manager's Drive              │
└──────────┬───────────────────┘
           │
           ▼
┌──────────────────────────────┐
│ MANAGER REVIEWS (Mobile)     │
│ - Reads MANAGER SUMMARY      │
│ - Edits MANAGER APPROVAL     │
│ - Approves or requests       │
│   changes                    │
└──────────┬───────────────────┘
           │
           ▼
┌──────────────────────────────┐
│ GOOGLE DRIVE SYNCS BACK      │
│ Approval syncs back to       │
│ local filesystem             │
└──────────┬───────────────────┘
           │
           ▼
┌──────────────────────────────┐
│ NEXT SESSION STARTS          │
│ AI reads approval and        │
│ continues, adjusts, or       │
│ rollsback as needed          │
└──────────────────────────────┘
```

**Per Session**:
- AI works on 1-3 sub-tasks
- Creates comprehensive session notes
- Manager reviews and approves
- AI continues based on feedback

**Manager Approval Options**:
- ✅ **APPROVED** - Continue as planned
- 🔄 **APPROVED WITH TASKS** - Add these tasks before continuing
- 🚨 **CHANGES NEEDED** - Redo this work
- 🚫 **ROLLBACK** - Revert to commit X
- ⏸️ **PAUSED** - Hold work, waiting for [reason]

---

## File Organization

### Root Level
```
{project-name}/
├── CLAUDE.md                    # AI context (read on every session)
├── tasks.md                     # Active task list
├── README.md                    # This file
├── .gitignore                   # Git ignore patterns
├── requirements.txt             # Python dependencies
├── .github/
│   └── PULL_REQUEST_TEMPLATE.md # PR template
└── [directories below]
```

### Development Directories
```
├── docs/                        # Research & planning documents
│   ├── README.md               # How to use docs
│   ├── 00_PROJECT_OVERVIEW.md  # Research skill output
│   ├── 01_Research_Brief.md
│   ├── 02_Market_Landscape.md
│   ├── 03_Technical_Feasibility.md
│   ├── 04_Go_To_Market.md
│   ├── 05_Risk_Assessment.md
│   ├── plan.md
│   └── PRD_[feature-name].md   # Feature PRDs
│
├── session-notes/               # Development session logs
│   ├── README.md               # How to use session notes
│   ├── _TEMPLATE.md            # Template for new sessions
│   ├── 2025-11-04-1200.md      # Session logs
│   └── 2025-11-05-1430.md
│
├── tasks/                       # Task generation templates
│   ├── create-prd.md           # PRD generation prompt
│   └── generate-tasks.md       # Task generation prompt
│
├── src/                         # Source code
│   └── __init__.py
│
└── tests/                       # Tests
    └── __init__.py
```

### Google Drive Mirror

Same structure syncs to:
```
G:\My Drive\AI_Projects\{ProjectName}\
├── docs/                       # Same as GitHub
├── session-notes/              # Synced for manager review
└── [any other docs]
```

---

## For AI Agents: Getting Started

### Session Startup Checklist

Every session, read in this order:

1. **CLAUDE.md** (5 min)
   - Project context, status, setup instructions
   - Strategic docs links
   - Code standards and architecture

2. **tasks.md** (5 min)
   - Current task list with hierarchical numbering
   - Which tasks are pending/in-progress/completed
   - Task descriptions and dependencies

3. **Last 2 session-notes files** (5 min)
   - What was approved/changed in previous sessions
   - Current branch state
   - Blockers from last time
   - Technical decisions made

4. **Relevant docs** (as needed)
   - **Starting new feature?** → Read PRD
   - **Technical implementation?** → Read 03_Technical_Feasibility.md
   - **Uncertain about scope?** → Read 00_PROJECT_OVERVIEW.md
   - **Making design decisions?** → Read 02_Market_Landscape.md

### Session Workflow

1. **Choose task** from tasks.md
   - Pick next un-started task
   - Or continue in-progress task
   - Check dependencies

2. **Implement**
   - Write code in src/
   - Write tests in tests/
   - Commit frequently with clear messages

3. **Test**
   - Run full test suite
   - Check coverage
   - Verify acceptance criteria met

4. **Session End** (after 1-2 hours or 3-5 tasks)
   - Copy `session-notes/_TEMPLATE.md` → `session-notes/YYYY-MM-DD-HHmm.md`
   - Fill all 3 sections:
     - MANAGER APPROVAL (set to PENDING)
     - MANAGER SUMMARY (what was done)
     - DETAILED NOTES (full technical context)
   - Commit and push
   - **STOP WORK** - Wait for manager approval

### Reading Session Approvals

Next session, check `session-notes/` for manager response:

```
MANAGER APPROVAL
Status: APPROVED
Response: Good work. Proceed with next tasks.
```

Based on status:
- **APPROVED** → Continue to next task
- **APPROVED WITH TASKS** → Add new tasks, continue
- **CHANGES NEEDED** → Redo work per feedback
- **ROLLBACK** → `git reset`, redo work
- **PAUSED** → Stop, wait for "proceed" message

---

## For Managers: Approving Work

### Review Workflow

1. **Open** latest session-notes file from Google Drive
   - Path: `AI_Projects/{ProjectName}/session-notes/YYYY-MM-DD-HHmm.md`

2. **Read MANAGER SUMMARY** section first
   - What was accomplished?
   - What's the blocker (if any)?
   - What's the recommendation?

3. **Check relevant docs** if needed
   - Does this match the PRD?
   - Are risks properly handled?
   - Is timeline realistic?

4. **Make decision**
   - ✅ **APPROVED**: Work looks good
   - 🔄 **APPROVED WITH TASKS**: Good, please add these
   - 🚨 **CHANGES NEEDED**: Redo before continuing
   - 🚫 **ROLLBACK**: Revert to commit X
   - ⏸️ **PAUSED**: Hold work pending [reason]

5. **Edit MANAGER APPROVAL** section
   ```
   Status: APPROVED
   Date Reviewed: 2025-11-05
   Response: Good work on JWT implementation. The approach matches our security requirements. Proceed with rate limiting middleware next.
   ```

6. **Save** file
   - Google Drive Desktop syncs changes back
   - AI reads approval next session

### Approval Examples

**Example 1: Approved**
```
Status: APPROVED
Date Reviewed: 2025-11-05
Response: Looks great! JWT implementation is solid. Proceed with next tasks as planned.
```

**Example 2: Changes Needed**
```
Status: CHANGES NEEDED
Date Reviewed: 2025-11-05
Response: Good progress on the rate limiting. Please make these adjustments before continuing:
1. Use Redis instead of in-memory (better for multi-server)
2. Add rate limiting to GET endpoints too
3. Lower limits by 50% (test with expected peak traffic)

Let me know when you've made these changes.
```

**Example 3: Rollback**
```
Status: ROLLBACK
Date Reviewed: 2025-11-05
Response: The password reset implementation needs a full redo. Issues found:
- Tokens should be 1 hour (not 24 hours)
- Need email verification before accepting new password
- Need rate limiting to prevent brute force

Please rollback to commit a7b3c9f and redo with these requirements.
```

---

## Key Concepts

### Two-Phase Task Generation (from ai-dev-tasks)

**Phase 1: Parent Tasks**
- Create 1.0, 2.0, 3.0 (major milestones)
- Get manager approval on overall approach
- Prevents rework if direction is wrong

**Phase 2: Sub-Tasks**
- Break each parent into 1.1, 1.2, 1.3, etc.
- Each sub-task fits in one session
- Execute incrementally with approval between

### Session-Based Development

**Each Session**:
- Duration: 1-2 hours
- Tasks: 1-3 sub-tasks
- Output: Session notes with manager approval
- AI stops and waits for approval before continuing

**Benefits**:
- Small, reviewable chunks of work
- Manager can provide feedback frequently
- Easy to adjust course if needed
- Clear progress checkpoints

### Manager Approval Workflow

**Not a GitHub-based workflow** (too heavy)

**Instead**:
- AI writes concise summary
- Manager reviews on phone via Google Drive
- Manager edits approval status
- Google Drive Desktop syncs back
- AI reads approval next session

---

## GitHub Features

### Branches
- `main` - Production code
- `feature/[name]` - Feature branches for development
- Always start session with: `git checkout -b feature/[feature-name]`

### Commits
- Write clear commit messages with imperative style
- Reference task numbers: "task 1.1: Implement JWT generation"
- One logical change per commit

### Pull Requests
Not used in this workflow - sessions are the approval mechanism

---

## Google Drive Integration

### What Syncs to Drive

Via Google Drive Desktop:
```
G:\My Drive\AI_Projects\{ProjectName}\
├── docs/                  # Research documents
├── session-notes/         # Session logs for manager review
└── [any other files]
```

### Workflow

1. **GitHub repo** is source of truth
2. **Google Drive Desktop** syncs `session-notes/` locally
3. **Manager reviews** on phone via Drive mobile app
4. **Google Drive Desktop** syncs changes back to local
5. **AI reads** changes from local filesystem

### No MCP Write Access Needed

- AI reads from local `G:\My Drive\...` path (filesystem)
- Google Drive Desktop handles sync
- Manager edits via Drive mobile app
- Changes sync back automatically
- No need for MCP write access!

---

## Dependencies

### Python
- Python 3.11+
- Dependencies listed in `requirements.txt`

### Google Drive Desktop
- Download: https://www.google.com/drive/download/
- Keep running for session-notes sync

### Git
- Git 2.30+
- GitHub account

---

## Common Tasks

### Starting a New Session
```bash
git pull origin main
git checkout -b feature/[feature-name]
# Read CLAUDE.md, tasks.md, last session-notes
# Begin work on next task
```

### Ending a Session
```bash
# Create session notes from template
cp session-notes/_TEMPLATE.md session-notes/2025-11-05-1430.md
# Fill all sections
git add session-notes/
git commit -m "session: Work on tasks 1.1, 1.2"
git push origin feature/[feature-name]
# WAIT FOR MANAGER APPROVAL
```

### After Manager Approval
```bash
git pull origin feature/[feature-name]
# Check MANAGER APPROVAL section of latest session-notes
# If APPROVED: continue to next task
# If CHANGES NEEDED: fix issues and resubmit
# If ROLLBACK: git reset --hard [commit-hash]
```

### Updating tasks.md
After session is approved:
```bash
# Mark completed tasks with session link
- [x] 1.1 Task name
  - Session: session-notes/2025-11-05-1430.md

# Update in-progress
- [ ] 1.2 Next task
  - Status: in progress
  - Session: [current]
```

---

## Troubleshooting

**Q: How do I know what to work on?**
- A: Check `tasks.md` for next pending task, or continue current in-progress task

**Q: Session notes not syncing to Drive?**
- A: Check Google Drive Desktop is running
- Manually copy if needed: `session-notes/` → Drive folder

**Q: Manager approval not visible?**
- A: Check Drive sync completed back to local
- Manually check Drive app for latest approval

**Q: Do I need to create a Pull Request?**
- A: No, session approval is your workflow, not PRs

**Q: How do I handle merge conflicts?**
- A: Keep feature branches short-lived to minimize conflicts
- If conflicts: resolve locally, add note in session-notes

---

## Resources

### This Template
- **GitHub**: This repository
- **Files**: See directory structure above
- **Docs**: [docs/README.md](docs/README.md)

### Related Tools
- **Research Skill**: [research-project-init](../Workflow_References/_Skills/research-project-init_v1/) - Generates research documents
- **Task Generation**: [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks) - Task methodology
- **Claude**: https://claude.ai - AI assistant for development

### Workflow Documentation
- **Session Management**: [session-notes/README.md](session-notes/README.md)
- **Research Integration**: [docs/README.md](docs/README.md)
- **PRD Creation**: [tasks/create-prd.md](tasks/create-prd.md)
- **Task Generation**: [tasks/generate-tasks.md](tasks/generate-tasks.md)

---

## License

This template is provided as-is. Use freely for your projects.

---

## Questions?

See related documentation:
- [CLAUDE.md](CLAUDE.md) - Project context
- [docs/README.md](docs/README.md) - Research workflow
- [session-notes/README.md](session-notes/README.md) - Session workflow
- [tasks.md](tasks.md) - Current tasks
