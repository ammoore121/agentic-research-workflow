# Agentic Research Workflow

> **Build web products with AI agents and human oversight**
>
> From business idea → research → planning → production code → manager approval

![Workflow](https://img.shields.io/badge/Status-Production--Ready-brightgreen)
![License](https://img.shields.io/badge/License-MIT-blue)
![Based-On](https://img.shields.io/badge/Based%20On-ai--dev--tasks-orange)

---

## What This Is

A complete, production-ready workflow system for building web products with **AI-assisted development** and **human oversight**. Perfect for solo founders, small teams, and anyone who wants to move from idea to code faster while maintaining quality and control.

**Key Features**:
- 🔍 **Research Automation** - Generate comprehensive market and technical research in 30 minutes
- 📋 **Intelligent Planning** - PRD generation and hierarchical task breakdown
- 🤖 **AI Development** - Session-based coding with automatic context management
- 👨‍💼 **Manager Oversight** - Review and approve work on your phone via Google Drive sync
- 📊 **Full Traceability** - Every decision documented, all history preserved in Git

**Perfect For**:
- SaaS products and web applications
- APIs and backend services
- Data products and analytics tools
- AI-powered features and integrations
- Solo founders building MVPs
- Small teams moving fast

---

## What Makes This Notable

### 1. Mobile-First Oversight
Most AI coding workflows assume you're at a computer reviewing code. This workflow is **built around reviewing work on your phone** via Google Drive sync. Manager approvals happen in 5-10 minutes while commuting—no IDE, no diff review needed. Just read summary, make decision.

### 2. Research-First Architecture
Starts before coding—**automating the "should we even build this?" decision**. Most AI dev tools assume you know what to build. This does:
- Competitive analysis
- Market sizing
- Technical feasibility assessment
- Go-to-market strategy
- Risk assessment

...before writing a single line of code. Addresses the higher-leverage decision point.

### 3. Session-Based Checkpointing
AI doesn't run until "done." **Works in discrete sessions with mandatory documentation and approval gates**. Creates natural stopping points that prevent runaway behavior while maintaining oversight without micromanagement.

### 4. Clean Separation of Concerns
```
GitHub = single source of truth (code, docs, tasks, history)
Google Drive = thin approval layer only (synced, no MCP write access needed)
```
Avoids the messy "which system is authoritative?" problem that plagues multi-tool workflows.

### 5. Async by Design
**Built for solo founders and small teams working asynchronously**. AI does deep work when you're not available, then pauses for input on key decisions. You're orchestrating, not babysitting.

### 6. Complete Traceability
**Every decision links back**: code → tasks → PRD → research. Wondering why something was built that way? There's a paper trail. Rare in AI-generated codebases.

### The Meta-Point
This treats **AI as a managed contractor**, not a copilot or autonomous agent. You define the project, check in at milestones, maintain control—without writing code yourself.

---

## How It Works: 5-Phase Workflow

```
┌─────────────┐       ┌──────────┐       ┌─────────┐       ┌────────────┐       ┌──────────┐
│ RESEARCH    │──────▶│ PLANNING │──────▶│  TASKS  │──────▶│ DEVELOPMENT│──────▶│ APPROVAL │
│ (30-60 min) │       │ (2 hours)│       │ (2 hrs) │       │ (Repeating)│       │ (Mobile) │
└─────────────┘       └──────────┘       └─────────┘       └────────────┘       └──────────┘
                                                                     ▲                    │
                                                                     └────────────────────┘
                                                                      Manager approves
                                                                      AI continues work
```

### Phase 1: Research (30-60 minutes)

**What**: Automated competitive analysis, market sizing, technical feasibility assessment

**Input**: Your business idea or feature description

**Process**:
1. Trigger the Claude Skill with your idea
2. Answer 5 clarifying questions
3. AI conducts research across 6 dimensions:
   - Competitive landscape (analyze top competitors)
   - Market sizing and trends
   - Technical feasibility and constraints
   - Go-to-market strategy
   - Risk assessment (legal, technical, financial)
   - Cost analysis

**Output**: 7 comprehensive research documents saved to your Google Drive

**Time**: 30-60 minutes | **Effort**: Minimal (answer questions)

---

### Phase 2: GitHub Setup (5 minutes)

**What**: Copy research into a structured GitHub repo

**Process**:
1. Create new GitHub repo from our template
2. Copy research documents from Drive to GitHub `/docs/` folder
3. Initial git commit
4. Update project context file (CLAUDE.md)

**Time**: 5 minutes | **Effort**: Copy/paste files

---

### Phase 3: Create PRD (1-2 hours)

**What**: Product Requirements Document from research findings

**Input**: Research documents + your answers to clarifying questions

**Process**:
1. AI reviews research
2. Generates 13-section PRD:
   - Overview and goals
   - User stories and functional requirements
   - Design and technical considerations
   - Success metrics
   - Links back to research sources
   - Implementation plan broken into phases

3. You review PRD
4. Manager approves or requests changes

**Output**: PRD saved to GitHub `/docs/`

**Time**: 1-2 hours | **Effort**: Review and approve

---

### Phase 4: Generate Tasks (2-4 hours)

**What**: Break PRD into implementable tasks with hierarchical structure

**Process**:
1. **Phase 4a - Parent Tasks** (1 hour)
   - Outline 4-6 major milestones (1.0, 2.0, 3.0, etc.)
   - Get manager approval on overall approach

2. **Phase 4b - Sub-Tasks** (1-3 hours)
   - Break each into 2-4 detailed steps (1.1, 1.2, 1.3, etc.)
   - Add acceptance criteria for each
   - Get approval to begin development

**Output**: Hierarchical task list in GitHub `tasks.md`

**Time**: 2-4 hours | **Effort**: Review and approve

---

### Phase 5: Development Sessions (Repeating)

**What**: AI works on tasks with automatic manager approval gates

**Workflow Per Session**:
```
START SESSION (15 min reading)
  ↓
  Read project context (CLAUDE.md, tasks.md, previous approvals)
  ↓
WORK (1-2 hours)
  ↓
  Implement task, write tests, commit code
  ↓
END SESSION (30 min documentation)
  ↓
  Write comprehensive session notes
  Set "Manager Approval" status to PENDING
  ↓
MANAGER REVIEWS (5-10 minutes on phone)
  ↓
  Read session summary
  Edit approval: APPROVED / CHANGES NEEDED / ROLLBACK / PAUSED
  ↓
NEXT SESSION
  ↓
  AI reads approval and continues accordingly
```

**Session Notes Include**:
- ✅ Manager Approval (at top - status, date, feedback)
- 📋 Manager Summary (concise 5-10 min read)
- 🤖 Detailed Notes (full technical context for AI)

**Manager Reviews On**: Phone via Google Drive mobile app (no special tools needed)

**Time**: Repeats for each development session

---

## Quick Start: 3 Steps

### Step 1: Install Dependencies

```bash
# Install Claude Skill
- Copy /claude-skill/research-project-init_v1/ into your Claude settings

# Install Google Drive Desktop
- Download: https://www.google.com/drive/download/
- Enable sync for AI_Projects/ folder

# GitHub Account & Git
- Create GitHub account: https://github.com
- Install Git: https://git-scm.com
```

### Step 2: Start Your First Project

```bash
# Run research (via Claude Skill)
"Research a SaaS tool for managing team tasks"
→ Research documents saved to Google Drive

# Create GitHub repo (from template)
Use our /github-template/ or:
gh repo create my-project --template ammoore121/agentic-research-workflow

# Copy research to GitHub and commit
git add docs/
git commit -m "docs: Add research"
git push
```

### Step 3: Start Planning and Coding

```bash
# Create PRD from research
Use /github-template/tasks/create-prd.md

# Generate tasks from PRD
Use /github-template/tasks/generate-tasks.md

# Begin development sessions
Read CLAUDE.md and tasks.md
Work on first task
Create session notes
Wait for manager approval
Continue
```

**Total Time**:
- Setup: 30 minutes (one-time)
- First project research: 45 minutes
- Planning phase: 3-4 hours
- Development: As needed (AI handles coding)

---

## What You Get

### 🔍 Research Automation
- Competitive analysis automatically conducted
- Market sizing and trends researched
- Technical constraints identified
- Go-to-market strategy developed
- Risks assessed upfront
- Comprehensive documents generated in 30-60 minutes

### 📋 Intelligent Planning
- PRD template with 13 sections
- Research findings integrated into requirements
- Hierarchical task structure (based on proven ai-dev-tasks methodology)
- Two-phase approval (parent tasks → sub-tasks)
- Clear acceptance criteria for each task

### 🤖 AI Development
- AI works autonomously on tasks
- Automatic context loading (previous sessions, decisions, research)
- Comprehensive code commits
- Tests written automatically
- Session documentation auto-generated

### 👨‍💼 Manager Oversight
- Review work summaries on your phone
- Approve/request changes/rollback without special tools
- Changes sync automatically via Google Drive
- Clear feedback loop between AI and manager
- Full audit trail in Git history

### 📊 Complete Documentation
- Every decision documented
- Full Git history preserved
- Research → PRD → Tasks → Code traceability
- Easy to onboard team members
- Ready for handoff or maintenance

---

## Files Included

### 📚 Documentation
- **docs/agentic-workflow-v2.md** - Complete workflow documentation (10,000+ words)
- **docs/setup-guide.md** - Step-by-step setup instructions
- **docs/CREDITS.md** - Full attribution and credits

### 🎯 Tools & Templates
- **claude-skill/** - Research automation skill (ready to install)
- **github-template/** - Complete GitHub project template
  - CLAUDE.md (AI context template)
  - tasks.md (task tracking template)
  - session-notes/ (session documentation template)
  - tasks/ (PRD and task generation prompts)
  - src/ & tests/ (code directories)
  - .gitignore, requirements.txt, etc.

### 📖 Examples
- **examples/web-saas-example.md** - Concrete walkthrough (building a SaaS tool)

---

## How to Share This With Friends

**Send them this link**:
```
github.com/ammoore121/agentic-research-workflow
```

**Tell them to**:
1. Clone or download the repo
2. Upload entire folder to Claude/Claude Code
3. Ask Claude: *"Explain this workflow and help me set it up for [their web product idea]"*
4. Claude will read everything and guide them through

**Or they can**:
1. Read README.md (you're here!)
2. Read docs/agentic-workflow-v2.md for complete details
3. Follow docs/setup-guide.md to install
4. Try examples/web-saas-example.md to see it in action

---

## Key Concepts

### GitHub-Primary Architecture

```
GITHUB = Single Source of Truth
  ├── All code (src/, tests/)
  ├── All documentation (docs/)
  ├── All tasks (tasks.md)
  └── All session logs (session-notes/)

GOOGLE DRIVE = Approval Layer (Sync Only)
  └── session-notes/ (synced for manager review)
     └── Manager edits approval status
     └── Syncs back to GitHub repo
```

**Why**:
- GitHub provides version history and audit trail
- Drive provides mobile-friendly manager approval
- No MCP write access needed (Google Drive Desktop handles syncing)
- Single source of truth prevents confusion

### Hierarchical Task Numbering

From proven methodology by [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks):

```
1.0 Implement Authentication     (Parent task)
  1.1 JWT token generation       (Sub-task 1 - 1 hour)
  1.2 Token validation           (Sub-task 2 - 1.5 hours)
  1.3 Password reset flow        (Sub-task 3 - 1.5 hours)

2.0 Add Rate Limiting            (Parent task)
  2.1 Design strategy            (Sub-task 1 - 1 hour)
  2.2 Implement middleware       (Sub-task 2 - 1.5 hours)
```

**Benefits**:
- Clear parent/child relationships
- Easy to reference ("work on 1.2")
- Manager can approve at two levels
- Each sub-task fits in one session

### Unified Session Notes

Single file per session with 3 sections:

1. **Manager Approval** (at top)
   - Status: APPROVED / CHANGES NEEDED / ROLLBACK / PAUSED
   - Date reviewed
   - Manager's feedback

2. **Manager Summary** (concise, 5-10 min read)
   - What was accomplished
   - What blockers exist
   - What decisions are needed
   - Next steps

3. **Detailed Notes** (full technical context)
   - Code changes with file links
   - Decisions made
   - Tests written
   - Blockers encountered
   - Context for next session

**Why unified**:
- Single file = single source of truth
- Manager approval at top = easy to find
- All context in one place = no information scattered

---

## Based On Industry Best Practices

### ai-dev-tasks Methodology

This workflow is heavily based on the excellent [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks) project (6.7k stars). We adopt their:

- **Hierarchical task numbering** (1.0, 1.1, 1.2)
- **Two-phase task generation** (parent approval → sub-task execution)
- **PRD template structure** (9 core sections)
- **Clarifying questions framework** (A/B/C/D format)
- **Incremental execution** (one task at a time with verification)

### Our Additions

We extend ai-dev-tasks with:

- **Research automation** (automated competitive analysis, market sizing)
- **Session management** (automatic context loading for AI continuity)
- **Manager approval workflow** (clear feedback loop without GitHub PRs)
- **Google Drive integration** (mobile-friendly oversight)
- **Unified session notes** (single file, not separate AI+manager docs)

See [docs/CREDITS.md](docs/CREDITS.md) for full attribution.

---

## Use Cases

### SaaS Product MVP
Research market demand → Plan MVP features → Develop MVP → Get manager feedback → Deploy

**Timeline**: 1-2 weeks from idea to deployed MVP

### API Backend
Research existing solutions → Plan API design → Implement endpoints → Approve and deploy

**Timeline**: 3-5 days from concept to deployed API

### Data Product
Research data sources → Plan pipeline → Build extraction/processing → Analyze results

**Timeline**: 1-2 weeks from data source to working product

### Feature Addition
Research user needs → Plan feature → Implement and test → Approve and release

**Timeline**: 2-5 days from idea to released feature

### AI Integration
Research existing models → Plan implementation → Build integration → Deploy

**Timeline**: 1 week from research to deployed AI feature

---

## Getting Help

### Documentation
- **docs/agentic-workflow-v2.md** - Complete reference (10,000+ words)
- **docs/setup-guide.md** - Step-by-step setup
- **examples/web-saas-example.md** - Concrete example walkthrough

### Inside the GitHub Template
- **github-template/README.md** - Project template guide
- **github-template/session-notes/README.md** - Session workflow details
- **github-template/docs/README.md** - Research integration guide
- **github-template/tasks/create-prd.md** - PRD generation prompt
- **github-template/tasks/generate-tasks.md** - Task generation prompt

### Ask Claude
Upload this entire repo to Claude and ask:
- "How do I set this up?"
- "Explain the workflow"
- "Help me with [specific phase]"
- "Show me an example of [specific part]"

Claude has access to all documentation and can guide you through.

---

## License

MIT License - Use freely for your projects, commercial or otherwise.

See [LICENSE](LICENSE) file for details.

---

## Credits

**Based On**:
- [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks) by snarktank (task management methodology)

**Includes**:
- Research automation via Claude Skills
- Session-based development workflow
- Manager approval integration with Google Drive
- GitHub template for project structure

**Inspiration**:
- Semi-autonomous agent workflows
- AI-assisted development best practices
- Manager oversight patterns

---

## What's Next?

Ready to build?

1. **Start with the setup guide**: [docs/setup-guide.md](docs/setup-guide.md)
2. **See it in action**: [examples/web-saas-example.md](examples/web-saas-example.md)
3. **Understand the full workflow**: [docs/agentic-workflow-v2.md](docs/agentic-workflow-v2.md)
4. **Use the GitHub template**: [github-template/](github-template/)

**Questions?** See [docs/setup-guide.md](docs/setup-guide.md#troubleshooting) troubleshooting section or ask Claude to help explain.

---

**Latest Update**: November 2025
**Status**: Production Ready
**Repository**: [github.com/ammoore121/agentic-research-workflow](https://github.com/ammoore121/agentic-research-workflow)
