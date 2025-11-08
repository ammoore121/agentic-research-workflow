# Documentation & Research

This folder contains all research, analysis, and planning documents generated during project initialization and planning phases.

## What Goes Here?

### From Research Phase
Documents created by the research-project-init Claude Skill:

- `00_PROJECT_OVERVIEW.md` - Executive summary with go/no-go recommendation
- `01_Research_Brief.md` - Hypothesis, research questions, success criteria
- `02_Market_Landscape.md` - Competitive analysis, market sizing, trends
- `03_Technical_Feasibility.md` - Data sources, tech stack, costs, timeline
- `04_Go_To_Market.md` - Target customers, pricing strategy, launch plan
- `05_Risk_Assessment.md` - Legal, technical, market, and financial risks
- `plan.md` - Action plan with next steps and milestones

### From Planning Phase
- `PRD_[feature-name].md` - Product requirements documents for features
- `RESEARCH_REFERENCES.md` - Links to all research sources and citations

### From Design Phase
- Architecture diagrams
- Database schemas
- API specifications
- UI mockups

---

## Workflow: Research to Code

### Step 1: Run Research Skill (on Google Drive)

Use the research-project-init Claude Skill:

1. Describe business idea / feature to research
2. Answer clarifying questions
3. Skill generates comprehensive research documents
4. **Saved to**: Your Google Drive (see setup guide)

**Documents created by skill**:
```
{ProjectName}/docs/
├── 00_PROJECT_OVERVIEW.md
├── 01_Research_Brief.md
├── 02_Market_Landscape.md
├── 03_Technical_Feasibility.md
├── 04_Go_To_Market.md
├── 05_Risk_Assessment.md
└── plan.md
```

### Step 2: Copy Docs to GitHub Repo

After research skill completes:

```bash
# Copy research docs from Drive to GitHub repo
# Navigate to your Google Drive synced folder and copy all .md files from {ProjectName}/docs/
# Paste them into {github-repo}/docs/

# Or use the command line (adjust path for your OS):
# macOS/Linux: cp ~/Drive/AI_Projects/{ProjectName}/docs/*.md docs/
# Windows: copy "{drive-letter}:\My Drive\AI_Projects\{ProjectName}\docs\*.md" docs\
```

### Step 3: Create Initial Commit

```bash
git add docs/
git commit -m "docs: Add research documents from research-project-init skill

- 00_PROJECT_OVERVIEW.md: Executive summary
- 01_Research_Brief.md: Research questions and hypothesis
- 02_Market_Landscape.md: Competitive analysis
- 03_Technical_Feasibility.md: Technical assessment
- 04_Go_To_Market.md: Go-to-market strategy
- 05_Risk_Assessment.md: Risk analysis
- plan.md: Action plan and milestones"

git push origin main
```

### Step 4: Generate PRD from Docs

Now that research is documented:

1. Review research documents
2. Use [tasks/create-prd.md](../tasks/create-prd.md) to generate PRD
3. PRD should reference research documents:
   ```
   ### Research Sources
   - Market analysis: 02_Market_Landscape.md
   - Technical feasibility: 03_Technical_Feasibility.md
   - Risks: 05_Risk_Assessment.md
   ```
4. Save PRD as `PRD_[feature-name].md` in this docs folder

### Step 5: Generate Tasks from PRD

1. PRD is approved by manager
2. Use [tasks/generate-tasks.md](../tasks/generate-tasks.md) to break into tasks
3. Tasks reference PRD for context
4. Begin development sessions per [session-notes workflow](../session-notes/README.md)

---

## Expected File Structure

```
docs/
├── README.md                          # This file
├── 00_PROJECT_OVERVIEW.md            # Research skill output
├── 01_Research_Brief.md              # Research skill output
├── 02_Market_Landscape.md            # Research skill output
├── 03_Technical_Feasibility.md       # Research skill output
├── 04_Go_To_Market.md                # Research skill output
├── 05_Risk_Assessment.md             # Research skill output
├── plan.md                           # Research skill output
├── PRD_[feature-name].md             # Generated from research
├── PRD_[feature-name-2].md           # Additional features
├── RESEARCH_REFERENCES.md            # All research sources and citations
├── architecture/                     # Design documentation
│   ├── system-architecture.md
│   ├── database-schema.md
│   └── api-specification.md
└── historical/                       # Old research/docs
    └── 2025-10-plan.md              # Archived planning docs
```

---

## How AI Agents Use These Docs

### Session Startup

AI reads docs **in this order**:

1. **CLAUDE.md** (5 min) - Project context and setup
2. **tasks.md** (5 min) - What tasks need work
3. **Last session-notes** (5 min) - What was approved
4. **Research docs** (as needed) - Deep dive on context
   - If starting on feature → Read relevant PRD
   - If doing technical work → Read 03_Technical_Feasibility.md
   - If uncertain about scope → Read 00_PROJECT_OVERVIEW.md

### During Development

AI references docs:
- **PRD**: To understand requirements
- **02_Market_Landscape.md**: If making design decisions
- **03_Technical_Feasibility.md**: If choosing tech stack
- **04_Go_To_Market.md**: If building customer-facing features
- **05_Risk_Assessment.md**: If making architectural decisions

### Documentation Decisions

When implementing features, AI checks docs for:
- What data sources are available? (03_Technical_Feasibility)
- What's the target user? (02_Market_Landscape)
- What's the success metric? (00_PROJECT_OVERVIEW)
- What risks apply? (05_Risk_Assessment)

---

## How Managers Use These Docs

### Decision Making

Reference research when:
- Approving session work → Check what's required in PRD
- Reviewing blockers → Check technical constraints in 03_Technical_Feasibility
- Validating scope → Check 00_PROJECT_OVERVIEW for go/no-go criteria
- Setting priorities → Check 02_Market_Landscape and 04_Go_To_Market

### Status Updates

Reference docs when reporting on project:
- "Market opportunity is $X per 02_Market_Landscape.md"
- "Technical constraints documented in 03_Technical_Feasibility.md"
- "Key risks listed in 05_Risk_Assessment.md"

### Course Corrections

If scope changes:
1. Review research docs to understand impact
2. Note change in session-notes
3. Update PRD or create new PRD
4. Get manager approval before continuing

---

## Research-to-Code Flow Diagram

```
┌─────────────────────────────┐
│ RESEARCH SKILL RUNS         │
│ (Claude web or desktop)     │
│                             │
│ Input: Business idea        │
│ Output: Research docs       │
│ Location: Google Drive      │
│           {ProjectName}/    │
│           docs/             │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│ COPY TO GITHUB              │
│                             │
│ docs/*.md                   │
│ → {repo}/docs/*.md          │
│                             │
│ Initial commit              │
│ Push to GitHub              │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│ CREATE PRD                  │
│                             │
│ Use: tasks/create-prd.md    │
│ Input: Research docs        │
│ Output: PRD_[name].md       │
│ Save in: docs/              │
│ Get approval: Manager       │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│ GENERATE TASKS              │
│                             │
│ Use: tasks/generate-tasks.md│
│ Input: PRD                  │
│ Output: tasks.md            │
│ Get approval: Parent tasks  │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│ EXECUTE SESSIONS            │
│                             │
│ Read: docs (as needed)      │
│ Work: tasks.md subtasks     │
│ Write: session-notes        │
│ Get approval: Manager       │
│ Continue: Next session      │
└─────────────────────────────┘
```

---

## Tips for Documentation

### For AI Agents Writing

✅ **DO**:
- Link to relevant research docs when making decisions
- Reference specific sections: "Per 03_Technical_Feasibility.md, we're using..."
- Document assumptions from research: "Research shows X, so we're building for Y"
- Update docs if understanding changes: "Initial assumption was wrong, here's why..."

❌ **DON'T**:
- Ignore what research says and build differently
- Make architectural decisions without checking constraints in 03_Technical_Feasibility.md
- Build features that don't align with market needs (check 02_Market_Landscape.md)

### For Managers Creating Research

✅ **DO**:
- Be thorough in research (skipping research == slower development)
- Include specific numbers: "Market is $X billion" not "big market"
- Include specific competitors: "Competitor A costs $X" not "competitors cost less"
- Include technical constraints: "Data costs $X per month" not "data is available"
- Include risks: "Payment processing requires PCI compliance" (from 05_Risk_Assessment.md)

❌ **DON'T**:
- Skip research ("we'll figure it out during development")
- Be vague ("market opportunity exists" without numbers)
- Assume tech stack ("we'll use Node" without evaluation)
- Ignore risks (they'll come back to haunt you)

---

## Research Skill Integration

### How to Run Research Skill

1. **Open Claude (Skills)**
2. **Find**: research-project-init skill
   - Install via: Setup guide (see main repository documentation)
3. **Trigger**: Use phrases like:
   - "Research [business idea]"
   - "Initialize research for [feature]"
   - "I want to research [opportunity]"
4. **Answer questions**: 5 quick clarifying questions
5. **Receive docs**: Research documents saved to Drive
6. **Copy to GitHub**: Move docs from Drive to this folder

### Research Skill Output

Skill generates 7 documents:

| Document | Purpose | Read by |
|----------|---------|---------|
| 00_PROJECT_OVERVIEW.md | Executive summary with go/no-go recommendation | Managers, AI agents |
| 01_Research_Brief.md | Hypothesis, questions, success criteria | AI agents during planning |
| 02_Market_Landscape.md | Competitive analysis, market sizing, trends | AI agents (features), managers (strategy) |
| 03_Technical_Feasibility.md | Data sources, tech stack, costs, timeline | AI agents (implementation), managers (budget) |
| 04_Go_To_Market.md | Target customers, pricing, launch plan | Managers, feature designers |
| 05_Risk_Assessment.md | Legal, technical, market, financial risks | Managers (decisions), AI agents (design) |
| plan.md | Action plan with milestones | Managers, AI agents (sequencing) |

---

## Keeping Docs Updated

### During Development

If understanding changes mid-project:
1. Note the change in session-notes
2. Update relevant doc (or create new one)
3. Tag manager attention (mention in MANAGER SUMMARY)
4. Commit changes with explanation

**Example**:
```bash
git commit -m "docs: Update technical feasibility based on development findings

During implementation of auth system, discovered:
- JWT library is faster than expected (0.5ms vs 2ms estimated)
- Rate limiting needs Redis (not in-memory) for multi-server setup
- Password reset should use email (not SMS) per customer feedback

Updated: 03_Technical_Feasibility.md with findings"
```

### After Project Completion

1. Move old research to `historical/` folder
2. Create summary document linking key decisions to research
3. Document what assumptions were correct vs wrong
4. Keep active docs for ongoing maintenance

---

## Troubleshooting

**Q: Where did the research docs go?**
- A: Check your Google Drive (synced local folder) under {ProjectName}/docs/
- They're in Drive until you copy them to GitHub

**Q: Should I update research docs after starting development?**
- A: Only if you discovered something fundamental was wrong
- Minor adjustments → Document in session notes
- Major findings → Update docs and tag manager

**Q: How do I reference research in code/tasks?**
- A: Link to specific docs and sections:
  - "Per 03_Technical_Feasibility.md, API costs $X per month"
  - "Per 02_Market_Landscape.md, top competitor offers Y feature"

**Q: What if research is outdated?**
- A: Run research skill again or create a new research doc
- Tag manager to review changes
- Update PRD based on new findings

---

## Related Documents

- **research-project-init skill**: Creates these research docs (see main documentation)
- **[create-prd.md](../tasks/create-prd.md)**: Uses research to generate PRD
- **[tasks.md](../tasks.md)**: Implementation tasks from PRD
- **[CLAUDE.md](../CLAUDE.md)**: Project context for all work
