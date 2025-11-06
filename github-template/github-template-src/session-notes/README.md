# Session Notes

This folder contains detailed logs of all development work sessions. It's the core of the AI-human collaboration workflow.

## What Are Session Notes?

Session notes are comprehensive work logs created at the end of each development session. They serve two purposes:

1. **AI-to-AI Communication**: Provides context for the next session (what was done, decisions made, blockers)
2. **AI-to-Human Communication**: Manager summary with approval section for guidance

## File Structure

```
session-notes/
├── README.md                      # This file
├── _TEMPLATE.md                   # Template for new sessions
├── 2025-11-04-1200.md            # Session from Nov 4, 12:00pm
├── 2025-11-05-1430.md            # Session from Nov 5, 2:30pm
└── ARCHIVE/                       # Old sessions (optional)
    └── 2025-10-28-1000.md
```

## Naming Convention

**Format**: `YYYY-MM-DD-HHmm.md`

- `YYYY-MM-DD`: Date of session
- `HHmm`: Start time in 24-hour format
- Example: `2025-11-05-1430.md` = November 5, 2025, 2:30 PM

**Multiple sessions same day?**
```
2025-11-05-0900.md  # Morning session
2025-11-05-1430.md  # Afternoon session
2025-11-05-1900.md  # Evening session
```

## How to Use Session Notes

### For AI Agents (Starting a Session)

**1. Read in this order**:
```
CLAUDE.md → tasks.md → Last 2 session-notes files
```

**2. Extract context**:
- What was approved last session?
- What's the current branch state?
- What blockers exist?
- What's next to work on?

**3. Work on assigned task**:
- Implement feature/fix
- Write tests
- Commit code
- Update CLAUDE.md if needed

**4. At session end** (when hitting ~2 hours or 3-5 tasks):
- Copy `_TEMPLATE.md` → `YYYY-MM-DD-HHmm.md`
- Fill in MANAGER APPROVAL (set to PENDING)
- Fill in MANAGER SUMMARY (what was done)
- Fill in DETAILED NOTES (full context for AI)
- Commit and push to GitHub
- **STOP WORK** - Wait for manager approval

### For Managers (Reviewing a Session)

**1. Open latest session-notes file** from Google Drive or GitHub

**2. Read MANAGER APPROVAL section first**:
```
✅ MANAGER APPROVAL

Status: PENDING
Date Reviewed: [empty]
Response: [empty]
```

**3. Read MANAGER SUMMARY section**:
- What tasks were completed?
- What's in progress?
- What decisions are needed?
- What's the next session plan?

**4. Make decision**:
- ✅ **APPROVED**: Work looks good, continue
- 🔄 **APPROVED WITH TASKS**: Good work, please add these tasks
- 🚨 **CHANGES NEEDED**: Redo this before continuing
- 🚫 **ROLLBACK**: Revert to commit X, redo differently
- ⏸️ **PAUSED**: Hold all work, waiting for [reason]

**5. Edit MANAGER APPROVAL section**:
```
✅ MANAGER APPROVAL

Status: APPROVED
Date Reviewed: 2025-11-05
Response:
```
Looks great! The JWT implementation matches our requirements. The token expiry looks good. Proceed with rate limiting middleware next.
```
```

**6. Save and sync**:
- Google Drive Desktop syncs back to the team's local copy
- AI reads this on next session start
- Continue work based on approval

### How Approval Flows Work

#### Option 1: APPROVED ✅
```
Status: APPROVED
Response: Good work. Proceed with next tasks as planned.
```
**Next session**: AI reads approval, continues to next task

#### Option 2: APPROVED WITH CHANGES 🔄
```
Status: APPROVED WITH TASKS
Response: Code looks good. Before continuing, please:
- Add rate limiting to GET endpoints too (not just POST)
- Add caching headers to API responses
```
**Next session**: AI updates tasks.md, works on new tasks before continuing

#### Option 3: CHANGES NEEDED 🚨
```
Status: CHANGES NEEDED
Response: The password reset implementation needs work:
- Tokens should expire in 1 hour (not 24 hours)
- Add email verification step before accepting new password
- Add rate limiting to password reset endpoint

Please redo this task and we'll review again.
```
**Next session**: AI reverts commit, redoes work per feedback

#### Option 4: ROLLBACK 🚫
```
Status: ROLLBACK
Response: Rollback to commit a7b3c9f and redo the rate limiting implementation.
We need to use Redis (not in-memory) due to multi-server deployment.
```
**Next session**: AI runs `git reset --hard a7b3c9f`, redoes work

#### Option 5: PAUSED ⏸️
```
Status: PAUSED
Response: Hold all development work. We're doing a security audit first.
Resume once you get the "proceed" message.
```
**Next session**: AI stops, waits for explicit "proceed" message

---

## Session Structure

Each session file has three main sections:

### 1. MANAGER APPROVAL (At Top)
- Where manager approves/rejects work
- Has status, date, and response fields
- **AI reads this first** to understand what to do next

### 2. MANAGER SUMMARY (What was done)
- Concise 5-10 minute read
- Key accomplishments, blockers, next steps
- Manager-friendly language

### 3. DETAILED NOTES (Full context)
- Everything AI needs to resume work
- Code changes, decisions, technical notes
- 10-15 minute read for AI

---

## Session Workflow Diagram

```
┌──────────────────────────┐
│ SESSION STARTS           │
│ AI reads:                │
│ - CLAUDE.md              │
│ - tasks.md               │
│ - Last session approval  │
└──────────────┬───────────┘
               │
               ▼
┌──────────────────────────┐
│ AI WORKS                 │
│ - Implement features     │
│ - Write tests            │
│ - Commit code            │
│ - ~1-2 hours work        │
└──────────────┬───────────┘
               │
               ▼
┌──────────────────────────┐
│ SESSION ENDS             │
│ AI creates session notes:│
│ - _TEMPLATE.md copied   │
│ - Fill all 3 sections   │
│ - Push to GitHub         │
└──────────────┬───────────┘
               │
               ▼
┌──────────────────────────────┐
│ GOOGLE DRIVE SYNCS           │
│ session-notes/ folder        │
│ syncs to manager's Drive     │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ MANAGER REVIEWS              │
│ (on phone, in Drive)         │
│ - Reads MANAGER SUMMARY      │
│ - Edits MANAGER APPROVAL     │
│ - Saves file                 │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ GOOGLE DRIVE SYNCS BACK      │
│ Changes sync back to local   │
│ AI sees approval next session│
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ NEXT SESSION STARTS          │
│ AI reads approval and        │
│ continues, adjusts, or       │
│ rollsback based on feedback  │
└──────────────────────────────┘
```

---

## Examples

### Example: Complete Session with Approval

**File**: `2025-11-05-1430.md`

```markdown
# Session: 2025-11-05 14:30-16:00

## ✅ MANAGER APPROVAL

Status: APPROVED
Date Reviewed: 2025-11-05
Response:
Excellent work! The JWT implementation is solid and well-tested. The decisions made (PyJWT library, 15min token expiry) align with our architecture.

Proceed with implementing the rate limiting middleware as planned.
```

**Result**: Next session, AI continues to task 1.2

---

### Example: Session with Needed Changes

**File**: `2025-11-05-1430.md`

```markdown
## ✅ MANAGER APPROVAL

Status: CHANGES NEEDED
Date Reviewed: 2025-11-05
Response:
The password reset implementation has a few issues:

1. Token expiry is 24 hours - should be 1 hour
2. Missing email verification step
3. No rate limiting on the reset endpoint (spam risk)

Please fix these and we'll review again. The base approach is good, just needs these refinements.
```

**Result**: Next session, AI reverts code, makes changes, and resubmits

---

## Tips for Session Notes

### For AI Agents Writing Notes

✅ **DO**:
- Be thorough in DETAILED NOTES (assume AI next session forgets everything)
- Be concise in MANAGER SUMMARY (they're reading on a phone)
- Include file links with line numbers (make code easy to find)
- Document decisions and why they were made
- List all blockers clearly (what's needed from manager?)
- Update task numbers as work completes (reference tasks.md)

❌ **DON'T**:
- Leave MANAGER APPROVAL empty (set it to PENDING)
- Make MANAGER SUMMARY too long (should be 5-10 min read)
- Forget to commit code before ending session
- Leave blockers undocumented
- Skip testing notes (what was tested? what wasn't?)

### For Managers Reviewing Notes

✅ **DO**:
- Read MANAGER SUMMARY first (not the detailed notes)
- Make decisions clear (APPROVED, APPROVED WITH TASKS, etc.)
- Provide specific feedback (not just "looks good")
- Be timely (review within 24 hours if possible)
- Use clear language (AI will read and understand)

❌ **DON'T**:
- Leave MANAGER APPROVAL blank (AI won't know what to do)
- Change MANAGER SUMMARY or DETAILED NOTES (write in MANAGER APPROVAL)
- Forget to edit the Status field
- Be vague ("this isn't right" - explain what needs fixing)
- Delay reviews (work stalls if approval takes 3 days)

---

## Integration with Other Files

### How Session Notes Connect to Other Files

```
CLAUDE.md
  ↓ (AI reads project context)

tasks.md
  ↓ (AI reads what tasks to work on)

session-notes/YYYY-MM-DD-HHmm.md
  ├─ AI reads last session's MANAGER APPROVAL
  ├─ AI works on tasks
  └─ AI writes new session notes

Manager Reviews
  ├─ Reads MANAGER SUMMARY
  └─ Writes MANAGER APPROVAL
```

### Links Between Files

Session notes reference:
- **tasks.md**: "Completed tasks: 1.0, 1.1, 1.2"
- **CLAUDE.md**: "Project context loaded from CLAUDE.md"
- **Research docs**: "See 02_Market_Landscape.md for competitive context"
- **Previous sessions**: "Based on approval from 2025-11-04-1430.md"

---

## Google Drive Sync

### How It Works

1. **GitHub repo** contains `session-notes/` folder
2. **Google Drive Desktop** syncs `session-notes/` to local filesystem
3. **Local path**: `G:\My Drive\AI_Projects\{ProjectName}\session-notes\`
4. **Manager reviews** on phone via Google Drive mobile app
5. **Changes sync back** to local filesystem
6. **AI reads** changes from local filesystem on next session

### Manual Sync (if needed)

If auto-sync doesn't work:
```bash
# Copy from GitHub repo to Drive
cp session-notes/YYYY-MM-DD-HHmm.md "G:\My Drive\AI_Projects\{ProjectName}\session-notes\"

# Or copy from Drive to GitHub
cp "G:\My Drive\AI_Projects\{ProjectName}\session-notes\YYYY-MM-DD-HHmm.md" session-notes/
```

---

## Archiving Old Sessions

After project is complete or milestone reached:

1. Create `session-notes/ARCHIVE/` folder
2. Move old sessions there
3. Keep recent sessions (last 2-3) in main folder
4. Keep a `_archive-index.md` listing archived sessions

**Example**:
```
session-notes/
├── 2025-11-10-1200.md  # Most recent
├── 2025-11-08-1430.md  # Recent
├── _TEMPLATE.md
├── ARCHIVE/
│   ├── 2025-11-05-1430.md
│   ├── 2025-11-04-1200.md
│   └── ...
```

---

## Troubleshooting

**Q: Session not showing in Google Drive?**
- A: Check that Google Drive Desktop is running and synced
- Manually copy file if needed

**Q: Manager's approval not visible to AI?**
- A: Check Google Drive sync completed
- Refresh local folder view
- Manually copy if needed

**Q: Session notes getting too long?**
- A: Trim DETAILED NOTES or archive old sessions
- Keep most recent 2-3 sessions visible

**Q: AI not following previous approvals?**
- A: Check AI is reading last session's MANAGER APPROVAL section
- Ensure CLAUDE.md has "read last session notes" in startup

---

## Related Documents

- **_TEMPLATE.md**: Template to copy for new sessions
- **tasks.md**: Active task list (referenced in sessions)
- **CLAUDE.md**: Project context (read before each session)
- **../docs/**: Research and planning documents
