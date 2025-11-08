# Agentic Workflow Documentation v2

**Last Updated**: 2025-11-05
**Status**: Active (production ready)
**Previous Version**: [agentic-workflow-documentation.md](agentic-workflow-documentation.md) (archived)

---

## Executive Summary

This document describes the complete workflow for AI-assisted development from research through deployment. It combines three components:

1. **research-project-init Claude Skill** - Generates comprehensive research documents
2. **GitHub Template Repository** - Provides project structure and task management
3. **Google Drive Integration** - Enables manager approval workflow without MCP write access

### What Changed from v1

| Aspect | v1 | v2 |
|--------|----|----|
| **Primary Store** | Hybrid (GitHub + Drive) | GitHub-primary with Drive mirror |
| **Session Notes** | Two separate files (AI + Manager) | Single unified file with 3 sections |
| **Manager Approval** | In separate folder | At TOP of session notes with date input |
| **Task Numbering** | Flat list | Hierarchical (1.0, 1.1, 1.2 from ai-dev-tasks) |
| **Task Generation** | Single phase | Two phases (parent → sub-tasks) |
| **MCP Write Access** | Required | Not needed (reads from local filesystem) |
| **PRD Template** | Basic | 13-section with research integration |
| **Workflow Tools** | Custom | Based on ai-dev-tasks methodology |

---

## Part 1: Architecture Overview

### GitHub-Primary with Drive Mirror

```
┌─────────────────────────────────────────────────────────┐
│ GITHUB (Single Source of Truth)                         │
│                                                         │
│ ├── docs/                  (research docs copied from  │
│ │   ├── 00_PROJECT_OVERVIEW.md     Drive)              │
│ │   ├── 01_Research_Brief.md                           │
│ │   ├── 02_Market_Landscape.md                         │
│ │   ├── 03_Technical_Feasibility.md                    │
│ │   ├── 04_Go_To_Market.md                             │
│ │   ├── 05_Risk_Assessment.md                          │
│ │   ├── plan.md                                        │
│ │   └── PRD_[feature].md   (generated during planning) │
│ │                                                      │
│ ├── src/                   (source code)               │
│ ├── tests/                 (test code)                 │
│ ├── session-notes/         (development logs)          │
│ ├── tasks/                 (PRD/task generation        │
│ │                          templates)                  │
│ ├── CLAUDE.md              (AI context)                │
│ └── tasks.md               (active task list)          │
│                                                        │
│ ✓ Version controlled                                   │
│ ✓ All history preserved                               │
│ ✓ Immutable once committed                            │
└─────────────────────────────────────────────────────────┘
                              │
                              │ Google Drive Desktop syncs
                              │ session-notes/ locally
                              ▼
┌─────────────────────────────────────────────────────────┐
│ GOOGLE DRIVE (Mirror & Approval Layer)                  │
│                                                         │
│ Via Google Drive Desktop sync:                          │
│ {ProjectName}/                                          │
│                                                         │
│ ├── docs/                  (mirrors GitHub)             │
│ │   ├── research docs                                  │
│ │   └── PRDs                                           │
│ │                                                      │
│ ├── session-notes/         (synced from GitHub)        │
│ │   ├── 2025-11-04-1200.md                            │
│ │   └── 2025-11-05-1430.md                            │
│ │   └── [manager edits MANAGER APPROVAL section]      │
│ │                                                      │
│ └── [syncs changes back to local filesystem]           │
│                                                        │
│ ✓ Mobile-accessible via Drive mobile app               │
│ ✓ Easy editing on phone                                │
│ ✓ No special permissions needed                        │
│ ✓ Changes sync back automatically                      │
└─────────────────────────────────────────────────────────┘
```

### Why This Architecture

**GitHub-Primary Benefits**:
- ✓ Single source of truth for all code and docs
- ✓ Full version history and audit trail
- ✓ Works with standard Git tools
- ✓ No vendor lock-in
- ✓ Supports CI/CD integration

**Drive Mirror Benefits**:
- ✓ Mobile-friendly approval workflow
- ✓ Simple HTTP POST integration (no complex APIs or OAuth flows)
- ✓ Manager can review on phone
- ✓ Automatic sync via Google Drive Desktop
- ✓ Separation of concerns (code vs approval)

**No MCP Write Access Needed**:
- AI reads from local filesystem (`G:\My Drive\...`)
- Google Drive Desktop app handles all syncing
- Manager edits in Drive mobile app
- Changes automatically sync back
- Result: Simple, reliable, no MCP complications

---

## Part 2: Complete Workflow

### Phase 0: Setup (One-Time)

1. **Install Google Drive Desktop**
   - Download: https://www.google.com/drive/download/
   - Enable sync for `AI_Projects/` folder
   - Creates local path: `G:\My Drive\AI_Projects\`

2. **Create base folder structure**
   - `G:\My Drive\AI_Projects\` - Main projects folder
   - `G:\My Drive\AI_Projects\Workflow_References\` - Skills and templates

3. **Have available**:
   - research-project-init Claude Skill
   - GitHub template repository
   - GitHub account and local git setup

---

### Phase 1: Research (Google Drive)

**Tool**: research-project-init Claude Skill

**Location**: Google Drive / Claude Skills interface

**Workflow**:
1. Trigger skill with business idea or feature description
2. Answer 5 clarifying questions (A/B/C/D format)
3. AI conducts research:
   - Competitive analysis (5-10 competitors)
   - Market sizing and trends
   - Technical feasibility assessment
   - Go-to-market strategy
   - Risk assessment
4. Generates 7 documents

**Output** (saved to Drive):
```
G:\My Drive\AI_Projects\{ProjectName}\docs\
├── 00_PROJECT_OVERVIEW.md      Executive summary
├── 01_Research_Brief.md         Hypothesis & questions
├── 02_Market_Landscape.md       Competitive analysis
├── 03_Technical_Feasibility.md  Tech assessment & costs
├── 04_Go_To_Market.md           Launch strategy
├── 05_Risk_Assessment.md        Legal/tech/market risks
└── plan.md                      Action plan & milestones
```

**Time**: 30-60 minutes
**Output**: 7 comprehensive research documents

---

### Phase 2: GitHub Repository Setup (~5 min manual)

**Location**: GitHub + Local Machine

**Steps**:

1. **Create GitHub repo from template**
   ```bash
   gh repo create {project-name} --template {template-repo-path}
   ```
   Or: GitHub UI → Use this template → Create repo

2. **Clone to local machine**
   ```bash
   git clone https://github.com/{owner}/{project-name}
   cd {project-name}
   ```

3. **Copy research docs from Drive to GitHub**
   ```bash
   # Copy from: G:\My Drive\AI_Projects\{ProjectName}\docs\
   # Paste into: {local-repo}\docs\
   ```
   Or: File Explorer → Drag and drop the files

4. **Initial commit**
   ```bash
   git add docs/
   git commit -m "docs: Add research documents from research-project-init skill

   - 00_PROJECT_OVERVIEW.md: Executive summary
   - 01_Research_Brief.md: Research questions
   - 02_Market_Landscape.md: Competitive analysis
   - 03_Technical_Feasibility.md: Technical assessment
   - 04_Go_To_Market.md: Go-to-market strategy
   - 05_Risk_Assessment.md: Risk analysis
   - plan.md: Action plan and milestones"

   git push origin main
   ```

5. **Update CLAUDE.md**
   - Replace placeholders with actual project info
   - Update GitHub URL
   - Link to research documents

6. **Update README.md**
   - Add project description
   - Add project-specific setup instructions

**Output**: GitHub repository with research docs, ready for planning
**Time**: 5 minutes

---

### Phase 3: Create PRD (Product Requirements Document)

**Tool**: PRD generation prompt (tasks/create-prd.md in your GitHub template)

**Location**: Local development (any Claude Code session)

**Workflow**:

**Step 1: Ask Clarifying Questions** (2 min)
- 5 structured questions about scope, goals, timeline, success metrics, dependencies
- Format: A/B/C/D options
- User responds with: "1A, 2C, 3B, 4B, 5A"

**Step 2: Generate PRD** (30-60 min)
- Create 13-section PRD:
  1. Overview
  2. Goals (measurable)
  3. User Stories
  4. Functional Requirements
  5. Non-Goals
  6. Design Considerations
  7. Technical Considerations
  8. Success Metrics
  9. Open Questions
  10. **Research Sources** (NEW - links to docs/)
  11. **Session Plan** (NEW - how implementation phases map to sessions)
  12. **Approval Status** (NEW - tracking approval)
  13. **Manager Notes** (NEW - feedback section)

**Step 3: Get Manager Approval**
- Manager reviews PRD
- ✅ Approves → Proceed to Phase 4
- 🔄 Changes needed → Revise and resubmit
- 🚫 Reject → Start over

**Output**: `docs/PRD_{feature-name}.md` (saved to GitHub)

**Time**: 30-90 minutes depending on complexity

---

### Phase 4: Generate Implementation Tasks

**Tool**: Task generation prompt (tasks/generate-tasks.md in your GitHub template)

**Location**: GitHub repo

**Workflow**:

**Phase 4a: Parent Task Outline** (1-2 hours)
1. Break PRD into 4-6 major milestones
2. Create parent tasks: 1.0, 2.0, 3.0, etc.
3. Brief description of each
4. Get manager approval on overall approach

**Phase 4b: Sub-Task Breakdown** (1-2 hours)
1. For each parent task, create 2-4 sub-tasks
2. Create: 1.1, 1.2, 1.3; 2.1, 2.2, 2.3; etc.
3. Add for each:
   - Description (what to implement)
   - Relevant files (what files to touch)
   - Acceptance criteria (definition of done)
   - Dependencies (what must come first)
   - Estimated time (30 min - 2 hours)
4. Get approval to begin development

**Output**: `tasks.md` with full hierarchical task list

**Time**: 2-4 hours depending on complexity

---

### Phase 5: Development Sessions

**Tool**: Claude Code (local development) + session-notes workflow

**Location**: GitHub repo + Google Drive (synced)

**Workflow Cycle**:

```
┌──────────────────────────────────────────────┐
│ SESSION START (Read in order)                │
│                                              │
│ 1. CLAUDE.md (5 min)                         │
│    Project context, setup, code standards    │
│                                              │
│ 2. tasks.md (5 min)                          │
│    What tasks need work?                     │
│                                              │
│ 3. Last 2 session-notes/ files (5 min)       │
│    What was approved? Any blockers?          │
│    Read MANAGER APPROVAL section first       │
│                                              │
│ 4. Relevant docs (as needed)                 │
│    PRD, research, architecture docs          │
└──────────────────────────┬───────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────┐
│ WORK (1-2 hours)                             │
│                                              │
│ - Pick next sub-task (1.1, 1.2, etc.)       │
│ - Implement feature/fix                      │
│ - Write tests (all tests must pass)          │
│ - Commit code with clear messages            │
│ - Check acceptance criteria met              │
│ - Update CLAUDE.md if needed                 │
└──────────────────────────┬───────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────┐
│ SESSION END (After 1-2 hours or 3-5 tasks)  │
│                                              │
│ 1. Copy session-notes/_TEMPLATE.md           │
│    → session-notes/YYYY-MM-DD-HHmm.md       │
│                                              │
│ 2. Fill MANAGER APPROVAL section             │
│    Status: PENDING                           │
│    Date Reviewed: [empty]                    │
│    Response: [empty]                         │
│                                              │
│ 3. Fill MANAGER SUMMARY section              │
│    What was completed (concise)              │
│    What blockers exist                       │
│    What's next                               │
│                                              │
│ 4. Fill DETAILED NOTES section               │
│    Full technical context for AI             │
│    Code changes, decisions, blockers         │
│                                              │
│ 5. Commit and push                           │
│    git add session-notes/                    │
│    git commit -m "session: Work on 1.1, 1.2"│
│    git push origin feature/[name]            │
│                                              │
│ 6. STOP WORK                                 │
│    Wait for manager approval                 │
└──────────────────────────┬───────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────┐
│ GOOGLE DRIVE SYNC                            │
│                                              │
│ Google Drive Desktop syncs                   │
│ session-notes/YYYY-MM-DD-HHmm.md            │
│ to: G:\My Drive\AI_Projects\{Project}\       │
│     session-notes/                           │
└──────────────────────────┬───────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────┐
│ MANAGER REVIEWS (Mobile)                     │
│                                              │
│ On phone, via Google Drive mobile app:       │
│                                              │
│ 1. Open AI_Projects/{Project}/session-notes/ │
│ 2. Open latest YYYY-MM-DD-HHmm.md            │
│ 3. Read MANAGER SUMMARY section              │
│ 4. Make decision:                            │
│    ✅ APPROVED - Continue as planned        │
│    🔄 APPROVED WITH TASKS - Add work items  │
│    🚨 CHANGES NEEDED - Redo this            │
│    🚫 ROLLBACK - Revert to commit X         │
│    ⏸️ PAUSED - Hold work                     │
│ 5. Edit MANAGER APPROVAL section:            │
│    Status: [choice above]                    │
│    Date Reviewed: YYYY-MM-DD                 │
│    Response: [feedback message]              │
│ 6. Save file                                 │
└──────────────────────────┬───────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────┐
│ GOOGLE DRIVE SYNCS BACK                      │
│                                              │
│ Google Drive Desktop syncs edited file back  │
│ to: {local-repo}/session-notes/              │
│                                              │
│ AI reads approval on next session start      │
└──────────────────────────┬───────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────┐
│ NEXT SESSION STARTS                          │
│                                              │
│ AI reads last session's MANAGER APPROVAL     │
│                                              │
│ If APPROVED: Continue to next task           │
│ If APPROVED WITH TASKS: Add tasks, continue  │
│ If CHANGES NEEDED: Redo work per feedback    │
│ If ROLLBACK: git reset, redo work            │
│ If PAUSED: Wait for explicit "proceed"       │
└──────────────────────────────────────────────┘
```

**Per Session Checklist**:
- ✓ Read CLAUDE.md, tasks.md, last approvals
- ✓ Pick next task (or continue in-progress)
- ✓ Implement with tests
- ✓ Commit code
- ✓ Create session notes with all 3 sections
- ✓ Push to GitHub
- ✓ STOP - Wait for approval
- ✓ Next session: Read approval, act accordingly

---

## Part 3: Session Management (Unified Notes)

### Session Notes Structure

Each session creates ONE file: `session-notes/YYYY-MM-DD-HHmm.md`

Format: `YYYY-MM-DD-HHmm` where:
- `YYYY-MM-DD` = Date (e.g., 2025-11-05)
- `HHmm` = Start time in 24-hour format (e.g., 1430 = 2:30 PM)

### Three Sections (Unified File)

#### Section 1: MANAGER APPROVAL (At Top)

```markdown
## ✅ MANAGER APPROVAL

Status: <!-- PENDING | APPROVED | APPROVED WITH TASKS | CHANGES NEEDED | ROLLBACK | PAUSED -->
Date Reviewed: <!-- YYYY-MM-DD -->
Response: <!-- Manager's feedback goes here -->
```

**Status Options**:

1. **PENDING** (default)
   - AI just created notes
   - Waiting for manager review
   - Status: `PENDING`

2. **APPROVED** ✅
   - Work meets requirements
   - Proceed with next tasks
   - Example response: "Good work! The JWT implementation is solid. Proceed with rate limiting next."

3. **APPROVED WITH TASKS** 🔄
   - Work is good, but add more work
   - Continue with new tasks added
   - Example: "Good progress. Before continuing, please: 1) Add caching headers, 2) Document API endpoints"

4. **CHANGES NEEDED** 🚨
   - Work doesn't meet requirements
   - Redo with feedback
   - Example: "The password reset needs: 1) 1-hour expiry (not 24hr), 2) Email verification step"

5. **ROLLBACK** 🚫
   - Revert to previous commit
   - Redo work differently
   - Example: "Rollback to commit a7b3c9f. Use Redis (not in-memory) for rate limiting."

6. **PAUSED** ⏸️
   - Stop all work
   - Wait for signal to resume
   - Example: "Hold work. We're doing security audit first. Resume when you get 'proceed' message."

#### Section 2: MANAGER SUMMARY (5-10 min read)

```markdown
## 📋 MANAGER SUMMARY

### Summary
[1-2 sentences: What was accomplished? Any blockers?]

### Completed Tasks
- 1.0 Task name
  - What was done
  - Result

### In Progress
- 2.0 Task name - 60% complete
  - Blocker: [What's blocking progress?]
  - Question: [What decision is needed?]

### 🚨 Needs Your Input
[Decisions, questions, recommendations for manager]

### Next Session Plan
1. [Task number and name]
2. [Task number and name]

### Metrics
- Time spent: X hours Y minutes
- Tasks completed: X of Y
- Code changes: +X lines, -Y lines
- Commits: N
- Tests: All passing / N failures
```

**Manager reads this to**:
- Understand what was done
- See what blockers exist
- Know what decisions are needed
- Plan next steps

#### Section 3: DETAILED NOTES (Full AI context)

```markdown
## 🤖 DETAILED NOTES

### Session Context
- Start time, files read, current branch
- Previous session and research references

### Tasks Worked On
- Task 1.0: What was implemented
- Task 1.1: Code changes with file links
- Task 1.2: Tests added and results

### Code Changes Summary
- Files modified, lines added/removed
- Git commits made

### Decisions Made
| Decision | Options | Choice | Reasoning |
|----------|---------|--------|-----------|

### Technical Context
- Architecture decisions
- Security considerations
- Performance impact
- Dependencies changed

### Testing Notes
- Coverage, test results, manual testing
- Edge cases handled

### Blockers & Challenges
- What blocked progress
- Impact on timeline
- Needs from manager

### Context for Next Session
- What's done vs remaining
- Current state (branch, uncommitted changes)
- File state needing attention
- Research references to review

### AI Notes
- Code quality assessment
- Test coverage assessment
- Tech debt added?
- Complex sections needing docs?
```

**AI reads this next session to**:
- Resume work with full context
- Know what was approved/rejected
- Understand decisions made
- See what's next

---

## Part 4: Task Management

### Hierarchical Task Numbering (from ai-dev-tasks)

**Format**:
- `1.0, 2.0, 3.0` = Parent tasks (major milestones)
- `1.1, 1.2, 1.3` = Sub-tasks (implementation steps)
- Each sub-task fits in one session (30 min - 2 hours)
- Each parent task takes 1-3 sessions

**Example**:
```
1.0 Implement Authentication System (4 hours)
  1.1 Implement JWT token generation (1 hour)
  1.2 Add token validation middleware (1.5 hours)
  1.3 Create password reset flow (1.5 hours)

2.0 Add Rate Limiting (3 hours)
  2.1 Design rate limiting strategy (1 hour)
  2.2 Implement middleware (1.5 hours)
  2.3 Add tests and monitoring (0.5 hours)

3.0 Create User Management (5 hours)
  3.1 Implement user CRUD endpoints (2 hours)
  3.2 Add user profiles and preferences (2 hours)
  3.3 Create admin dashboard (1 hour)
```

### Two-Phase Task Generation

**Phase 1: Parent Tasks** (for manager approval)
1. Create 4-6 parent tasks from PRD
2. Brief description and estimated time
3. Submit for manager approval on overall approach
4. Benefit: Can adjust direction before detailed breakdown

**Phase 2: Sub-Tasks** (for execution)
1. Once parent tasks approved, break into sub-tasks
2. Add: description, relevant files, acceptance criteria, dependencies, time estimate
3. Ready for execution
4. Benefit: Clear implementation steps, one task per session

### tasks.md Format

```markdown
# Project Tasks

## 0.0 Create Feature Branch
- [ ] 0.1 Create and checkout feature branch

## 1.0 [Phase/Feature Name]
- [ ] 1.1 [Sub-task]
  - Status: not started
  - Session: [link to session notes]
  - Description: What needs implementing?
  - Relevant files: [list of files affected]
  - Acceptance Criteria:
    - [ ] Criterion 1
    - [ ] Criterion 2
  - Dependencies: [What must be done first?]
  - Estimated Time: 1 hour

- [ ] 1.2 [Sub-task]
  - Status: in progress
  - Session: [link to session notes]
  - ...

## 2.0 [Next Phase]
- [ ] 2.1 [Sub-task]
  - ...
```

### Task Status

After each session:
- Update `tasks.md`
- Mark completed tasks with `[x]` and add session link
- Mark in-progress with `[ ]` and current session
- Mark blocked with `[!]` and reason

---

## Part 5: Approval Workflow

### How Manager Approves (Mobile)

**Workflow**:

1. **Open Google Drive** on phone
2. **Navigate** to `AI_Projects/{ProjectName}/session-notes/`
3. **Open** latest `YYYY-MM-DD-HHmm.md` file
4. **Read** MANAGER SUMMARY section (takes 5-10 min)
5. **Make decision** on what to approve
6. **Edit file** - Scroll to MANAGER APPROVAL section at top
7. **Fill in fields**:
   - Status: (choose one)
   - Date Reviewed: (today's date)
   - Response: (your feedback/decision)
8. **Save** file (Google Drive saves automatically)

### Example Approvals

**Example 1: APPROVED**
```
Status: APPROVED
Date Reviewed: 2025-11-05
Response: Excellent work on JWT implementation! The approach is solid and matches our security requirements. Token expiry timing looks good. Proceed with rate limiting middleware as planned.
```

**Example 2: APPROVED WITH TASKS**
```
Status: APPROVED WITH TASKS
Date Reviewed: 2025-11-05
Response: Good progress on authentication! Before moving to rate limiting, please:
1. Add rate limiting to existing GET endpoints (not just new ones)
2. Add caching headers to API responses
3. Document the token refresh flow

Add these as tasks 1.4, 1.5, 1.6 in tasks.md and proceed.
```

**Example 3: CHANGES NEEDED**
```
Status: CHANGES NEEDED
Date Reviewed: 2025-11-05
Response: Password reset implementation needs work:
1. Token expiry should be 1 hour (you have 24 hours)
2. Add email verification step before accepting new password
3. Add rate limiting to prevent brute force attacks

Please fix these and resubmit for review. The base approach is good, just needs these refinements.
```

**Example 4: ROLLBACK**
```
Status: ROLLBACK
Date Reviewed: 2025-11-05
Response: Rollback to commit a7b3c9f and redo rate limiting middleware.

Initial approach (in-memory) won't work because we're deploying to multiple servers. Use Redis instead. This matches our infrastructure plan better.

After rollback, redo 2.2 with Redis implementation.
```

**Example 5: PAUSED**
```
Status: PAUSED
Date Reviewed: 2025-11-05
Response: Hold all development work on this project.

We're doing a security audit first and need to finalize authentication requirements. Will send updated requirements by 2025-11-10.

Resume when you get explicit "proceed" message.
```

### How AI Reads Approvals

**Next session startup**:
1. Read `session-notes/` folder
2. Open most recent file
3. Read MANAGER APPROVAL section immediately
4. Parse Status field
5. Based on Status:
   - **PENDING**: Check if same file - if so, wait. If new session, previous approval is missing.
   - **APPROVED**: Continue with next task
   - **APPROVED WITH TASKS**: Update `tasks.md` with new tasks, work on those first
   - **CHANGES NEEDED**: Redo previous work per feedback, resubmit
   - **ROLLBACK**: `git reset --hard [commit-hash]`, redo work
   - **PAUSED**: Stop work, wait for explicit "proceed" message

---

## Part 6: Integration Points

### How Everything Connects

```
RESEARCH SKILL (Google Drive)
│
├─ Generates 7 research documents
├─ Saved to: G:\My Drive\AI_Projects\{Project}\docs\
│
▼

GITHUB REPOSITORY SETUP (5 min)
│
├─ Copy docs from Drive → GitHub /docs/
├─ Initial commit with research
├─ Update CLAUDE.md with project info
│
▼

PRD CREATION (60-90 min)
│
├─ Uses research docs for context
├─ Creates 13-section PRD
├─ Links to research sources
├─ Gets manager approval
├─ Saved to: docs/PRD_{feature}.md
│
▼

TASK GENERATION (2-4 hours)
│
├─ Phase 1: Parent tasks from PRD
├─ Get manager approval
├─ Phase 2: Sub-tasks with acceptance criteria
├─ Saved to: tasks.md
│
▼

DEVELOPMENT SESSIONS (Repeating cycle)
│
├─ AI works on sub-tasks (1-2 hours per session)
├─ Implements, tests, commits code
├─ Creates session notes with approval section
├─ Pushes to GitHub
├─ Google Drive Desktop syncs to Drive
│
├─ Manager reviews MANAGER SUMMARY on phone
├─ Manager edits MANAGER APPROVAL section
├─ Saves to Drive
│
├─ Google Drive Desktop syncs back
├─ AI reads approval, continues/adjusts/rollbacks
│
└─ Loop until all tasks complete

▼

DEPLOYMENT & MAINTENANCE
│
├─ All history in GitHub
├─ All decisions documented in session-notes
├─ All research preserved in docs
└─ Project ready for handoff or maintenance
```

### File References

**Research docs** link to:
- Used to create PRD
- Referenced during design decisions
- Preserved in GitHub `/docs/`

**PRD** links to:
- Research docs (Research Sources section)
- Session plan (what sessions implement it)
- Referenced during task generation

**Tasks** link to:
- PRD (what requirement they implement)
- Session notes (which session worked on them)
- Code commits (proof of work)

**Session Notes** link to:
- Tasks (which tasks were completed)
- Research docs (for context)
- Previous sessions (for continuity)
- Code commits (what changed)

---

## Part 7: File Organization

### GitHub Repository Structure

```
{project-name}/
│
├── README.md                   Main project guide (from template)
├── CLAUDE.md                   AI agent context (customized)
├── tasks.md                    Active task list (hierarchical)
│
├── .gitignore                  Git ignore patterns
├── requirements.txt            Python dependencies
│
├── .github/
│   └── PULL_REQUEST_TEMPLATE.md
│
├── docs/                       Research & planning
│   ├── README.md              How to use docs
│   ├── 00_PROJECT_OVERVIEW.md
│   ├── 01_Research_Brief.md
│   ├── 02_Market_Landscape.md
│   ├── 03_Technical_Feasibility.md
│   ├── 04_Go_To_Market.md
│   ├── 05_Risk_Assessment.md
│   ├── plan.md
│   └── PRD_[feature-name].md
│
├── session-notes/              Development session logs
│   ├── README.md              How to use sessions
│   ├── _TEMPLATE.md           Template (copy for new sessions)
│   ├── 2025-11-04-1200.md     Session logs
│   └── 2025-11-05-1430.md
│
├── tasks/                      Task generation prompts
│   ├── create-prd.md          PRD generation prompt
│   └── generate-tasks.md      Task generation prompt
│
├── src/                        Source code
│   ├── __init__.py
│   ├── models/
│   ├── services/
│   └── utils/
│
└── tests/                      Tests
    ├── __init__.py
    └── [test files]
```

### Google Drive Mirror Structure

```
G:\My Drive\AI_Projects\{ProjectName}\
│
├── docs/                       Synced from GitHub /docs/
│   ├── research documents
│   └── PRDs
│
├── session-notes/              Synced from GitHub /session-notes/
│   ├── 2025-11-04-1200.md     (manager reviews & edits these)
│   └── 2025-11-05-1430.md
│
└── [any other files stored in Drive]
```

### Why This Structure

**GitHub repo**:
- Single source of truth
- Full version history
- Immutable once committed
- Supports CI/CD

**Google Drive mirror**:
- Mobile access for manager review
- Easy editing on phone
- No special tools needed
- Changes sync automatically

---

## Part 8: Tools & Dependencies

### Required Components

#### 1. Claude Skill: research-project-init
- **Location**: Claude Skills (installed per setup guide)
- **Purpose**: Generate comprehensive research documents
- **Inputs**: Business idea, clarifying questions
- **Outputs**: 7 research documents saved to Drive
- **Time**: 30-60 minutes
- **Cost**: Included in Claude subscription

#### 2. GitHub Template Repository
- **Location**: See setup guide (your fork or the original template)
- **Purpose**: Provides project structure, task management, session workflow
- **Includes**:
  - CLAUDE.md template
  - tasks.md template
  - session-notes templates
  - PRD generation prompt
  - Task generation prompt
  - .gitignore and other boilerplate
- **Usage**: Clone/use as template for new projects

#### 3. Google Drive Desktop
- **Download**: https://www.google.com/drive/download/
- **Purpose**: Sync session-notes folder for mobile manager access
- **Setup**: Install and enable sync for `AI_Projects/` folder
- **Result**: Creates `G:\My Drive\AI_Projects\` local path
- **Cost**: Free (part of Google Drive)

#### 4. GitHub Account & Git
- **GitHub**: https://github.com
- **Git**: https://git-scm.com
- **Purpose**: Version control for code and documentation
- **Usage**: Clone repos, create branches, commit, push
- **Cost**: Free (with GitHub Free tier)

#### 5. Claude Code or Other IDE
- **Tool**: Claude Code (this VSCode extension), VS Code, PyCharm, etc.
- **Purpose**: Local development and testing
- **Usage**: Write code, run tests, commit changes
- **Cost**: Varies (Claude Code, VS Code free, etc.)

### Optional Components

- **GitHub Advanced**: GitHub Actions (CI/CD), GitHub Projects (issue tracking)
- **Cloud Infrastructure**: AWS, Google Cloud, Azure for deployment
- **Analytics**: Tools for measuring success metrics
- **Collaboration**: Slack for team communication

---

## Part 9: Decision Log

### Why GitHub-Primary (Not Hybrid)

**v1 Problem**: Split between GitHub and Drive created confusion
- "Which version is current?"
- "Did changes sync?"
- Harder to track history

**v2 Solution**: GitHub is single source of truth
- **All docs** go to GitHub (research, PRD, code)
- **Only approval layer** on Drive (session-notes for manager review)
- **Clear separation**:
  - GitHub = immutable history
  - Drive = approval gate

**Benefits**:
- ✓ One source of truth
- ✓ Full audit trail in Git
- ✓ Easy to rollback
- ✓ No sync conflicts
- ✓ CI/CD compatible

---

### Why Unified Session Notes (Not Separate Files)

**v1 Problem**: Two separate files
- session-notes/ (AI-to-AI, detailed)
- Actions_Review/ (AI-to-Manager, summary)
- AI had to read BOTH files
- Decisions documented in one, context in another
- Easy to miss approvals

**v2 Solution**: Single unified file with 3 sections
- MANAGER APPROVAL (at top, date input)
- MANAGER SUMMARY (concise review)
- DETAILED NOTES (full context)
- **One file = one source of truth**

**Benefits**:
- ✓ Simpler for AI (read one file)
- ✓ Simpler for manager (everything in one place)
- ✓ Easier to find approvals (at top)
- ✓ Better correlation (summary + detailed in same file)
- ✓ Fewer sync issues

---

### Why No MCP Write Access Needed

**Original Concern**: "Need MCP write access to save to Drive"

**Solution Discovery**: Google Drive Desktop syncs files
- AI reads from local path: `G:\My Drive\...`
- This is regular filesystem access, not MCP
- Google Drive Desktop handles all syncing
- Manager edits on phone
- Changes sync back automatically

**Result**:
- ✓ No MCP write access needed
- ✓ No security concerns
- ✓ Simple and reliable
- ✓ Works offline (sync when connected)
- ✓ Automatic backup

---

### Why ai-dev-tasks Integration

**Problem**: Custom task numbering was flat and unclear
- "What's the difference between tasks?"
- "Which tasks go together?"
- Hard to track progress across phases

**Solution**: Use proven methodology from ai-dev-tasks
- Hierarchical numbering (1.0, 1.1, 1.2)
- Clear parent/child relationships
- Two-phase approach (parent → sub-tasks)
- Each sub-task fits in one session

**Benefits**:
- ✓ Clear structure (easy to reference)
- ✓ Proven in open source (6.7k stars)
- ✓ Manager can approve at two levels
- ✓ Incremental execution
- ✓ Easy progress tracking

---

### Why PRD Template with Research Integration

**Problem**: PRDs didn't reference research findings
- "Why are we building this?"
- "What are the constraints?"
- Decision-making disconnected from research

**Solution**: 13-section PRD that includes:
- Research Sources (links to docs/)
- Session Plan (how implementation maps to sessions)
- Approval Status (tracking)
- Manager Notes (feedback)

**Benefits**:
- ✓ Research informs all decisions
- ✓ Easy to understand "why"
- ✓ Traceability from research → PRD → tasks → code
- ✓ Manager can easily review context

---

## Part 10: Quick Reference

### Phase Durations

| Phase | Time | Manual Work | Approval |
|-------|------|-------------|----------|
| Phase 1: Research | 30-60 min | None | N/A |
| Phase 2: Setup | 5 min | Copy files | N/A |
| Phase 3: PRD | 60-90 min | None | ✓ Required |
| Phase 4: Tasks | 2-4 hours | None | ✓ Required (2 times) |
| Phase 5: Dev | Variable | Frequent | ✓ Per session |

### Manager Approval Decisions

```
┌─────────────────────────────────────────┐
│ MANAGER SEES SESSION SUMMARY            │
└─────────────────────────────────────────┘
                │
         ┌──────┴──────┬──────────┬──────────┬────────┐
         │             │          │          │        │
         ▼             ▼          ▼          ▼        ▼
       APPROVED    CHANGES    ROLLBACK    PAUSED    APPROVED
       (Continue)  NEEDED     (Redo)      (Wait)    WITH TASKS
                   (Redo)                            (Add work)
```

### File Quick Links

```
GitHub Repo Structure:
├── CLAUDE.md          → Read for project context
├── tasks.md           → Read for what to work on
├── session-notes/     → Create/read for session logs
├── docs/              → Read for requirements/design
│   ├── PRD_*.md       → Requirements for feature
│   └── 0*_*.md        → Research findings
└── src/               → Write code here

Google Drive Sync:
G:\My Drive\AI_Projects\{Project}\
├── docs/              → Same as GitHub (informational)
├── session-notes/     → Synced from GitHub (manager edits)
```

### Common Commands

```bash
# Start new session
git pull origin main
git checkout -b feature/[name]
# Read CLAUDE.md, tasks.md, last session notes
# Work on next task...

# End session
cp session-notes/_TEMPLATE.md session-notes/YYYY-MM-DD-HHmm.md
# Fill all three sections
git add session-notes/
git commit -m "session: Work on tasks X.X, X.X"
git push origin feature/[name]
# WAIT FOR MANAGER APPROVAL

# After approval
git pull origin feature/[name]
# Check MANAGER APPROVAL section
# If APPROVED: continue to next task
# If ROLLBACK: git reset --hard [commit]
# etc.
```

---

## Conclusion

This workflow creates a seamless integration between:
1. **Research** (comprehensive upfront investigation)
2. **Planning** (clear requirements and tasks)
3. **Development** (incremental sessions with approval)
4. **Management** (mobile-friendly oversight)

The GitHub-primary architecture with Drive mirror gives you:
- ✓ Single source of truth
- ✓ Full version history
- ✓ Manager accessibility
- ✓ Clear approval workflow
- ✓ No special tools required
- ✓ Scalable to multiple projects

All while maintaining context, preventing rework, and enabling rapid iteration.

---

**Document Version**: v2
**Last Updated**: 2025-11-05
**Status**: Ready for production use
**Previous**: [agentic-workflow-documentation.md](agentic-workflow-documentation.md)
