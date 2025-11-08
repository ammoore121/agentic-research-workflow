# Example: Building a SaaS Tool from Idea to MVP

**Project**: Meeting Notes AI - A SaaS tool that automatically transcribes, summarizes, and extracts action items from team meetings

**Timeline**: 2 weeks from research to deployed MVP

This example walks through the complete workflow using a realistic SaaS product.

---

## Phase 1: Research (Day 1 - 45 minutes)

### The Idea

> "Build a SaaS tool that transcribes meeting videos, summarizes discussions, and automatically extracts action items. Target: Product teams and engineering orgs."

### Running the Research Skill

1. **Trigger the skill**
   ```
   I want to build a SaaS tool that helps teams:
   - Automatically transcribe meetings
   - Get AI-generated summaries
   - Extract action items
   - Search meeting history

   Target customers: Product teams, engineering orgs, distributed companies
   ```

2. **Answer clarifying questions**
   - Scope: B (Medium, 2-4 weeks)
   - Primary goal: B (Add new capability)
   - Success metric: B (Customer adoption rate, target 50+ signups first month)
   - Timeline: B (Soft deadline, target launch in 2 weeks)
   - Dependencies: A (Standalone feature)

3. **Research Output** (7 documents generated)

### Sample Research Results

**00_PROJECT_OVERVIEW.md** (excerpt)
```
Meeting Notes AI - Executive Summary

GO/NO-GO: GO

Opportunity: $500M+ TAM (all companies have meetings)
Competitive: 3-5 direct competitors (mostly desktop), none fully web-based
Technical: Feasible with existing APIs (Whisper for transcription, GPT for summaries)
Cost: ~$2-5 per meeting at scale (API costs)
Timeline: 2-week MVP realistic

Recommendation: BUILD. Clear market need, technology exists, low risk.
```

**02_Market_Landscape.md** (excerpt)
```
Competitive Analysis:

1. Otter.ai (Leader)
   - $120/year subscription
   - Focuses on personal notes
   - Limited action item extraction
   - Strength: Accuracy

2. Fireflies.io (Growing)
   - $99-200/month team plans
   - Team features
   - Action item extraction
   - Strength: Team collaboration

3. Sembly (Niche)
   - $129/month
   - Focuses on action items
   - Limited meeting notes
   - Strength: Task integration

Gap: No web-based collaborative tool with transcription + summaries + action items

Market Sizing:
- TAM: $500M+ (all organizations)
- SAM: $5B (product/engineering teams)
- SOM: $50M (realistic capture, 10k customers @ $500/year)

Pricing Opportunity: $200-500/month for team plans (premium positioning)
```

**03_Technical_Feasibility.md** (excerpt)
```
Technology Stack Options:

Option A: Python Backend (Recommended)
- Whisper API for transcription ($0.006/min)
- GPT-4 for summaries ($0.01-0.03 per summary)
- PostgreSQL for storage
- React frontend
- AWS/Google Cloud hosting
- Estimated cost: $200/month for 100 meetings

MVP Scope:
- Web upload interface
- Transcription via Whisper API
- Summary generation via GPT-4
- Action item extraction
- Meeting search
- User authentication
- Team management

Timeline:
- Backend + API: 1 week
- Frontend: 1 week
- Testing + deployment: 2 days
- Total: 10 days (realistic)

Costs:
- Development: Your time (AI-assisted)
- Hosting: $100-200/month
- API costs: $200-500/month (at 100 meetings)
- Total: $300-700/month to start
```

---

## Phase 2: GitHub Setup (Day 1 - 5 minutes)

### Create Repository

```bash
gh repo create meeting-notes-ai --template {your-template-url}
git clone https://github.com/{username}/meeting-notes-ai
cd meeting-notes-ai
```

### Copy Research to GitHub

```bash
# Copy from Google Drive to GitHub
# Navigate to your synced Google Drive folder and copy docs/*.md files
# Paste them into the docs/ folder in your repository

# Then commit

git add docs/
git commit -m "docs: Add research from research-project-init skill

- Market analysis shows $500M TAM
- 3-5 competitors, but no web-based collaborative tool
- Technical feasibility confirmed (Whisper + GPT-4)
- MVP timeline: 2 weeks realistic
- Go/no-go: GO"
git push origin main
```

### Update CLAUDE.md

```markdown
# Meeting Notes AI

## Metadata
GitHub: {username}/meeting-notes-ai
Status: In Development
Owner: You (@{username})
Last Updated: 2025-11-06

Strategic Docs: See docs/ folder
- Market Analysis: docs/02_Market_Landscape.md
- Technical Stack: docs/03_Technical_Feasibility.md
- Go-To-Market: docs/04_Go_To_Market.md
- Risks: docs/05_Risk_Assessment.md

## Project Summary
A web-based SaaS tool that automatically transcribes meetings, generates summaries,
and extracts action items. Target: Product teams and engineering orgs.

Competitive advantage: Only web-based, collaborative solution with all three features.

## Development Setup
Language: Python 3.12 with React frontend
API Keys Needed: OpenAI (for GPT-4), Whisper API

## For AI Agents
Work on tasks in hierarchical order: 1.0 → 1.1 → 1.2 → etc.
Each session focuses on 1-3 sub-tasks.
Session notes go to session-notes/ folder.
Manager approves after each session before continuing.
```

---

## Phase 3: Create PRD (Day 2-3 - 2 hours)

### Using the PRD Template

1. **Trigger PRD generation**
   ```
   Create a PRD for Meeting Notes AI SaaS tool using these research documents:
   - 00_PROJECT_OVERVIEW.md
   - 02_Market_Landscape.md
   - 03_Technical_Feasibility.md

   Use the PRD template from tasks/create-prd.md
   ```

2. **AI asks clarifying questions**
   - Pricing model? B (Subscription SaaS)
   - Primary revenue driver? A (Monthly subscription)
   - Initial target market? A (Product/engineering teams)
   - Feature vs reliability priority? A (Must be reliable)
   - MVP vs v1? A (Focus on MVP)

### Generated PRD Structure

**docs/PRD_meeting-notes-ai.md**

```markdown
# PRD: Meeting Notes AI - MVP

## 1. Overview
Meeting Notes AI is a web-based SaaS tool that automatically transcribes meetings,
generates summaries, and extracts action items. Target: Product and engineering teams.

## 2. Goals (Measurable)
- Get first 50 paying customers by month 2
- 95% transcription accuracy (measured monthly)
- 24-hour satisfaction score >4/5
- Less than 2 minutes from upload to results

## 3. User Stories
- As a product manager, I want to transcribe team meetings so I don't miss decisions
- As an engineer, I want to search past action items so I remember what I committed to
- As a team lead, I want to share meetings with my team so everyone's aligned

## 4. Functional Requirements
### 4.1 Core Features
1. Video/audio upload (MP4, MOV, WAV formats)
2. Automatic transcription via Whisper API
3. AI summary generation (key points, decisions)
4. Action item extraction (who, what, when)
5. Search across meetings
6. Meeting history/archive
7. User authentication
8. Team management (invite teammates)

### 4.2 Out of Scope (MVP)
- Real-time meeting transcription
- Calendar integration
- Slack integration (phase 2)
- Custom models
- API access

## 5. Non-Goals
- Not a general meeting recorder (focused on post-meeting analysis)
- Not competing on transcription accuracy alone
- Not building enterprise features in MVP

## 6. Design Considerations
- Simple, clean UI (record → upload → get results)
- Mobile-responsive design
- One-click sharing with team
- Search prominent (users want to find past items)

## 7. Technical Considerations
Option A: Outsource transcription to Whisper API
- Cost: $0.006 per minute of audio
- Reliability: High (OpenAI owned)
- Quality: 95%+ accuracy
- CHOSEN for MVP (fast to market)

Option B: Self-hosted transcription model
- Cost: $500 GPU to start
- Reliability: Good
- Quality: 90% accuracy
- Too complex for MVP

## 8. Success Metrics
| Metric | Target | Timeline |
|--------|--------|----------|
| Signups | 50 | Month 1-2 |
| MRR | $5,000 | Month 2 |
| Transcription accuracy | 95% | Continuous |
| User satisfaction | 4/5 | Monthly |
| Free trial conversion | 20% | Ongoing |

## 9. Research Sources
- Market Analysis: 02_Market_Landscape.md
- Technical Feasibility: 03_Technical_Feasibility.md
- Competitive Positioning: 02_Market_Landscape.md (Comparison section)

## 10. Session Plan
Phase 1: Backend API (1 week)
  - Weeks 1-2: Implement transcription, summary, action item extraction endpoints

Phase 2: Frontend (1 week)
  - Weeks 3-4: Web interface, upload, results display, search

Phase 3: Auth & Deployment (3 days)
  - Week 5: User auth, team management, deploy to production

## 11. Approval Status
Status: PENDING MANAGER APPROVAL
Created: 2025-11-06
```

### Manager Approves

Manager reads PRD and approves:
```
Status: APPROVED

Looks great! Love the focus on the "why" (executives need organized meeting notes).
The pricing positioning ($200-500/month) is aggressive but justified.

Approved to proceed with task generation.
```

---

## Phase 4: Generate Tasks (Day 3-4 - 3 hours)

### Phase 4a: Parent Tasks

```
Break this PRD into parent tasks and get approval:

Meeting Notes AI MVP Implementation Plan

Estimated: 2 weeks, 6 parent milestones
```

**AI generates**:
```
Parent Tasks:

1.0 Backend Infrastructure (3 days)
    - Set up project structure, database, API framework
    - Configure Whisper API and GPT-4 access

2.0 Transcription Feature (3 days)
    - Implement audio upload endpoint
    - Integrate Whisper API
    - Store transcriptions

3.0 Summary & Action Items (2 days)
    - Implement summary generation via GPT-4
    - Extract action items from summary
    - Format and store results

4.0 Frontend - Upload & Display (3 days)
    - Create web interface
    - Upload form
    - Results display
    - Search functionality

5.0 Authentication & Teams (2 days)
    - User authentication
    - Team management
    - Permission system

6.0 Testing & Deployment (2 days)
    - End-to-end testing
    - Performance optimization
    - Deploy to production
```

**Manager approves parent tasks**:
```
Status: APPROVED

Good breakdown. Realistic timeline.
Note: Can you start with transcription working well? That's our core value.
Everything else is secondary.

Proceed with detailed sub-tasks.
```

### Phase 4b: Detailed Sub-Tasks

```
Expand each parent task into detailed sub-tasks with acceptance criteria
```

**Example: Task 1.0 - Backend Infrastructure**

```markdown
## 1.0 Backend Infrastructure (3 days)

### 1.1 Set Up Project Structure
- [ ] Create Python project
  - Status: not started
  - Description: Initialize Python 3.12 project with virtual env, install dependencies
  - Relevant files:
    - requirements.txt
    - src/
    - src/config.py
  - Acceptance Criteria:
    - [ ] Python project initialized with venv
    - [ ] All dependencies installed
    - [ ] .env file configured with API keys
    - [ ] Tests run successfully
  - Estimated time: 30 min
  - Dependencies: None

### 1.2 Set Up Database
- [ ] Create PostgreSQL schema
  - Status: not started
  - Description: Create database, tables for meetings, users, teams
  - Relevant files:
    - src/models/
    - src/database.py
    - migrations/
  - Acceptance Criteria:
    - [ ] PostgreSQL database created
    - [ ] Tables: users, teams, meetings, transcriptions, summaries
    - [ ] Relationships defined
    - [ ] Migrations working
  - Estimated time: 1 hour
  - Dependencies: 1.1

### 1.3 Set Up API Framework
- [ ] Create FastAPI application
  - Status: not started
  - Description: Set up FastAPI with authentication middleware
  - Relevant files:
    - src/main.py
    - src/api/
    - src/middleware/
  - Acceptance Criteria:
    - [ ] FastAPI app running on localhost:8000
    - [ ] Health check endpoint working
    - [ ] Authentication middleware in place
    - [ ] CORS configured for frontend
  - Estimated time: 1 hour
  - Dependencies: 1.1, 1.2

### 1.4 Configure External APIs
- [ ] Set up Whisper API and GPT-4 access
  - Status: not started
  - Description: Configure OpenAI API clients, set up rate limiting
  - Relevant files:
    - src/config.py
    - src/services/transcription.py
    - src/services/summarization.py
  - Acceptance Criteria:
    - [ ] OpenAI API keys configured
    - [ ] Whisper client initialized
    - [ ] GPT-4 client initialized
    - [ ] Error handling for API limits
  - Estimated time: 30 min
  - Dependencies: 1.1
```

**tasks.md** includes all tasks:

```markdown
# Meeting Notes AI - Tasks

## 0.0 Create Feature Branch
- [ ] 0.1 Create and checkout feature branch

## 1.0 Backend Infrastructure
- [ ] 1.1 Set up project structure
- [ ] 1.2 Set up database
- [ ] 1.3 Set up API framework
- [ ] 1.4 Configure external APIs

## 2.0 Transcription Feature
- [ ] 2.1 Create upload endpoint
- [ ] 2.2 Integrate Whisper API
- [ ] 2.3 Handle transcription storage
- [ ] 2.4 Add error handling

## 3.0 Summary & Action Items
- [ ] 3.1 Create summarization endpoint
- [ ] 3.2 Extract action items
- [ ] 3.3 Format and store results
- [ ] 3.4 Add tests

## 4.0 Frontend
- [ ] 4.1 Create React app
- [ ] 4.2 Build upload interface
- [ ] 4.3 Display results
- [ ] 4.4 Implement search

## 5.0 Authentication & Teams
- [ ] 5.1 User registration/login
- [ ] 5.2 JWT authentication
- [ ] 5.3 Team management
- [ ] 5.4 Permission checks

## 6.0 Testing & Deployment
- [ ] 6.1 Integration tests
- [ ] 6.2 Performance optimization
- [ ] 6.3 Deployment to production
```

**Manager approves tasks**:
```
Status: APPROVED

Good detail level. Each sub-task is 1-3 hours, realistic.
I like that transcription is early (core value).

Ready to start development.
```

---

## Phase 5: Development Sessions (Days 5-14)

### Session 1: Backend Setup (Day 5)

**Start of session**:
- Read CLAUDE.md, tasks.md, previous approvals
- Check current status: Starting task 1.1

**Work** (2 hours):
```
Completed:
✅ 1.1 Set up project structure
✅ 1.2 Set up database
✅ 1.3 Set up API framework (partial)

In Progress:
⏸️ 1.3 Set up API framework (60% complete)

Code changes:
- src/main.py - FastAPI application
- src/models/ - Database models
- requirements.txt - Dependencies added
- 2 commits: a7b3c9f, d4e8f2a
```

**End of session** (Create session-notes/2025-11-06-1430.md):

```markdown
# Session: 2025-11-06 14:30-16:00

## ✅ MANAGER APPROVAL

Status: PENDING
Date Reviewed:
Response:

---

## 📋 MANAGER SUMMARY

### Summary
Completed project structure setup and database schema. API framework 60% complete
(core endpoints working, need to finish auth middleware).

### Completed
- 1.1 Project structure initialized with virtual env and dependencies
- 1.2 PostgreSQL database with users, teams, meetings tables
- 1.3 FastAPI app running with health endpoint

### In Progress
- 1.3 Auth middleware (90 minutes left estimated)

### 🚨 Needs Your Input
None - proceeding as planned. Will complete auth tomorrow.

### Next Session
1. Finish API framework (1.3)
2. Start configuring external APIs (1.4)
Estimated time: 2 hours

### Metrics
- Time: 2 hours
- Tasks: 2.5 of 14 completed (18%)
- Code: 150 lines added, 20 lines removed
- Commits: 2

---

## 🤖 DETAILED NOTES

### Tasks Completed
1.1 Set up project structure
- Created Python 3.12 project with virtual env
- Installed: fastapi, sqlalchemy, pydantic, python-dotenv
- Created project structure:
  - src/main.py
  - src/config.py
  - src/models/
  - src/api/
  - tests/
- .env.example created with required API keys
- All tests pass

1.2 Set up database
- PostgreSQL database created
- Tables created:
  - users (id, email, password_hash, created_at)
  - teams (id, name, owner_id, created_at)
  - meetings (id, team_id, title, uploaded_at, status)
  - transcriptions (id, meeting_id, text, confidence)
  - summaries (id, meeting_id, summary, action_items)
- Foreign key relationships set up
- Migration system configured

1.3 Set up API framework (partial)
- FastAPI app initialized in src/main.py
- CORS configured for localhost:3000 (React frontend)
- Health check endpoint: GET /health → {"status": "ok"}
- Database connection middleware in place
- Request/response logging configured
- Error handling middleware set up

### Decisions Made
1. Used FastAPI (not Flask): FastAPI has built-in async support, perfect for
   long-running transcription jobs
2. PostgreSQL (not SQLite): Needed for production database, team collaboration features
3. SQLAlchemy ORM: Standard Python ORM, easy testing

### Blockers
None currently. Everything proceeding smoothly.

### Next Session
1. Complete 1.3 - Auth middleware (JWT implementation)
2. Start 1.4 - Configure external APIs (Whisper, GPT-4)

Estimated time: 2 hours
```

### Manager Reviews & Approves

Manager reads on phone:
```
Status: APPROVED

Good progress! Project structure is clean, database schema looks right.
The decision to use FastAPI is good - async will help with transcription jobs.

Continue with authentication middleware. That's crucial for the team features.
```

### Session 2: Complete Backend Setup (Day 6)

**Session notes excerpt**:
```
## ✅ MANAGER APPROVAL

Status: APPROVED

Session: 2025-11-07 10:00-12:00

Completed:
✅ 1.3 API framework complete with JWT auth
✅ 1.4 OpenAI APIs configured

In Progress: None

### Metrics
- Time: 2 hours
- Tasks: 4 of 14 completed (29%)
- Code: 280 lines added
- Commits: 3

### Next Session
Start transcription feature (2.1 - Create upload endpoint)
Estimated time: 2 hours
```

Manager approves: `Status: APPROVED - Moving fast! Let's hit transcription next.`

### Session 3: Upload Endpoint (Day 7)

**Session notes excerpt**:
```
## ✅ MANAGER APPROVAL

Status: APPROVED

Session: 2025-11-07 14:30-16:00

Completed:
✅ 2.1 Create upload endpoint (POST /meetings/upload)
✅ 2.2 Integrate Whisper API

In Progress:
⏸️ 2.3 Handle transcription storage (50%)

### Summary
Created upload endpoint that accepts audio files, calls Whisper API,
and returns transcription. Response time: 15 seconds for 5-min audio.

### Blockers
Need to decide: Should we queue long transcriptions (15+ min) or process sync?
Recommend: Queue jobs for >10 minutes (user experience)
```

Manager responds:
```
Status: APPROVED WITH TASKS

Queue jobs for >10 minutes audio. Add new task:
6.1a: Implement job queue for long transcriptions (before deployment)

This is important for user experience. Don't want 30-min calls blocking uploads.
```

**AI updates tasks.md**:
```
## 6.0 Testing & Deployment
- [ ] 6.1 Integration tests
  - [ ] 6.1a Implement job queue for transcriptions >10min  [NEW]
- [ ] 6.2 Performance optimization
```

### Sessions 4-14: Continue Development

Each session follows the same pattern:
1. Read CLAUDE.md, tasks.md, last approvals
2. Work on assigned tasks (1-3 per session)
3. Create session notes with all 3 sections
4. Commit and push
5. Wait for manager approval
6. Manager approves or requests changes
7. Continue

**Summary of remaining development**:

**Days 8-9**: Transcription feature complete
- Upload, Whisper integration, storage, error handling

**Days 10-11**: Summary & Action Items feature
- GPT-4 summaries, action item extraction, formatting

**Days 12-13**: Frontend development
- React app, upload interface, results display, search

**Days 14-15**: Authentication & Deployment
- User login, team management, production deployment

**Day 16**: Testing & Launch
- End-to-end testing, performance tuning, deploy to production

---

## Phase 5 Summary: What Happened

**Total time**: 12 working days (realistic for AI-assisted development)

**Output**:
- ✅ 100+ tests written (all passing)
- ✅ ~3,000 lines of backend code
- ✅ ~2,000 lines of frontend code
- ✅ 15+ commits with clear messages
- ✅ Comprehensive documentation
- ✅ Production-ready application

**Manager involvement**:
- ✅ Approved PRD (2 hours)
- ✅ Approved tasks (1 hour)
- ✅ Reviewed session summaries (5-10 min per session, 12 sessions = 1 hour total)
- ✅ Made 3 decisions (job queue, API choice, deployment strategy)
- **Total manager time**: 4 hours over 2 weeks

**Cost**:
- Development time: Your time (AI-assisted, so much faster)
- API costs: $500-1,000/month in operation
- Hosting: $200-300/month
- Total: Cheap compared to hiring developers

---

## The Result: Meeting Notes AI MVP

### Live at: myna-ai.example.com (hypothetical)

**Features working**:
- Upload audio/video files
- Automatic transcription (95% accuracy)
- AI-generated summaries
- Action item extraction
- Team sharing
- Meeting search
- User authentication
- Team management

**Pricing**: $199/month for teams (first 50 customers get lifetime discount)

**Customers**: First month gets 25 signups, Month 2 gets 50 signups

**Feedback**: Users love the simplicity and accuracy. NPS score: 47 (strong)

**Next phases**:
- Slack integration (Phase 2)
- Calendar integration (Phase 3)
- Custom AI models (Phase 4)

---

## Key Learnings from This Example

### 1. Research Drives Everything
The research phase identified:
- Market opportunity ($500M TAM)
- Competitive gap (no web-based collaborative tool)
- Technology viability (Whisper + GPT-4)
- Business model (SaaS subscription)

Without research, you might have built the wrong thing.

### 2. Two-Phase Tasks Prevent Rework
Approving parent tasks first let manager validate overall approach.
No major direction changes mid-development.

### 3. Session Approvals Keep Things Aligned
Manager didn't need to understand code, just review 2-paragraph summaries.
One decision (job queue) prevented poor user experience.

### 4. Clear Traceability Matters
Every feature traced back to:
- PRD requirement → Task → Session → Code commit

Easy to explain "why we built this" and easy to onboard new team members.

### 5. AI Acceleration is Real
- ~14 business days for working MVP
- ~4 hours of manager time (minimal oversight)
- High quality code with tests
- Production-ready from day 1

---

## What You Could Do Next

**Short term** (Days 16-30):
- Get 100+ signups from Product Hunt launch
- Refine based on user feedback
- Fix bugs reported by early users

**Medium term** (Weeks 5-12):
- Phase 2: Slack integration (people use Slack, not email)
- Phase 3: Calendar integration (knows when meetings happen)
- Phase 4: Custom models (train on company data)

**Long term** (Months 4-12):
- Enterprise features (SSO, advanced permissions)
- API access (let customers build on top)
- Marketplace (integrate with other tools)

---

## How This Workflow Enabled This Timeline

**Without this workflow** (traditional approach):
- Spend 1 month writing requirements (PRD)
- Spend 1 month planning architecture
- Spend 4 weeks building backend
- Spend 4 weeks building frontend
- Spend 2 weeks testing
- Total: 14 weeks

**With this workflow** (AI-assisted):
- Research: 1 day (automated)
- Planning: 2 days (with AI input)
- Development: 12 days (AI codes, you review)
- Testing: Built in during sessions
- Total: 2 weeks

**10x faster** because:
- Research is automated
- AI writes the code
- Manager approvals are lightweight (5-10 min)
- Tests are written as you build
- No context switching (AI maintains context)

---

## Questions About This Example?

1. **How realistic is the timeline?**
   A: Very realistic with AI assistance. Backend is straightforward (CRUD + API calls).
   Frontend is standard React. The main complexity is integrating external APIs (Whisper, GPT-4),
   which is handled quickly.

2. **What if things go wrong?**
   A: Session approval gates catch issues early. If manager sees a problem in summary,
   they can ask for changes before continuing.

3. **What about scaling?**
   A: MVP handles 100 meetings/month. Scaling to 1000s would need additional work
   (caching, job queues, database optimization), but that's month 3+ work.

4. **Could this be done faster?**
   A: Maybe 1 week with very focused scope, but you'd be cutting corners. 12 days
   is "fast and good quality."

5. **Can I customize the workflow?**
   A: Absolutely! This is a template. Your project might need different phases,
   different checkpoints, different manager involvement levels.

---

## To Use This Example for Your Own Project

1. **Replace "Meeting Notes AI"** with your idea
2. **Run the research phase** with your idea
3. **Follow the same structure** for PRD and tasks
4. **Adjust timeline** based on complexity
5. **Keep the approval workflow** (it works)

The workflow is proven. Your project just needs to follow the phases.

---

**Last Updated**: November 2025
**Example Status**: Hypothetical (but realistic timeline and workflow)
**Next Step**: Try it yourself! Start with research phase.
