# Generate Implementation Tasks from PRD

**Based on**: [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks) methodology, adapted for session-based workflow

## What This Does

Breaks down a PRD into implementation tasks using hierarchical numbering (1.0, 1.1, 1.2, etc.). Tasks are designed to fit within session work (1-3 tasks per ~2-3 hour session).

## When to Use

- After PRD has been approved
- When ready to begin implementation
- When reprioritizing work mid-project
- When tasks need refinement

---

## Task Generation Workflow

### Phase 1: Outline Parent Tasks

Create 4-6 parent tasks (1.0, 2.0, 3.0, etc.) that represent major milestones.

**Format**:
```
1.0 [Phase/Feature Name]
2.0 [Next Phase/Feature Name]
3.0 [Final Phase/Feature Name]
```

**Guidelines**:
- Each parent task should take 1-3 sessions (4-8 hours)
- List parent tasks with brief descriptions
- Get approval before breaking into sub-tasks

### Phase 2: Outline Sub-Tasks

For each parent task, create 2-4 sub-tasks (1.1, 1.2, 1.3, etc.).

**Format**:
```
1.0 Authentication System
  1.1 Implement JWT token generation
  1.2 Add token validation middleware
  1.3 Create password reset flow
```

**Guidelines**:
- Each sub-task should take 30min-2 hours (fits in one session)
- Sub-tasks should be implementable independently
- Include relevant files and dependencies

### Phase 3: Add Details to Tasks

For each task, document:
- Description (what needs to be done)
- Relevant files (what files are affected)
- Tests needed (what testing is required)
- Acceptance criteria (how do we know it's done)
- Dependencies (what must be done first)

---

## Task Template (For Each Sub-Task)

Use this structure for each sub-task in `tasks.md`:

```markdown
- [ ] 1.1 [Task Title]
  - **Status**: not started
  - **Session**: [Link to session notes]
  - **Description**: What needs to be implemented?
  - **Relevant files**:
    - src/[file1.py](src/file1.py)
    - tests/[test_file1.py](tests/test_file1.py)
  - **Notes**: Technical context or approach
  - **Dependencies**: Tasks that must complete first
  - **Acceptance Criteria**:
    - [ ] Code implemented and tested
    - [ ] All tests passing
    - [ ] Documentation updated
    - [ ] [Specific requirement met]
  - **Estimated Time**: X hours
```

---

## Generating Tasks from PRD

### Step 1: Extract Implementation Phases

From PRD sections (4. Functional Requirements, 6. Design Considerations, 7. Technical Considerations), identify major phases:

**From PRD**:
- 4.1 Feature Set → Parent task
- 4.2 Integration Points → Parent task
- 6.1-6.3 User Experience → Parent task
- 7.2 Technical Approach → Parent task

**Create parent tasks**:
- 1.0: Core feature implementation
- 2.0: Integration and data handling
- 3.0: Testing and polish
- 4.0: Documentation and deployment

### Step 2: Break Into Sub-Tasks

For each parent task, identify specific implementation steps:

**Example: Parent Task 1.0 - Core Authentication**

Sub-tasks:
```
1.1 Implement JWT token generation
  - Create JWTManager class
  - Add encode/decode methods
  - Handle token expiry

1.2 Add token validation middleware
  - Create middleware function
  - Extract token from request
  - Validate and decode token
  - Attach user to request context

1.3 Create password reset flow
  - Generate reset tokens
  - Send reset email
  - Validate reset token
  - Update password
```

### Step 3: Document Each Task

For each sub-task, add:

**Relevant Files**:
- Which files will be created/modified?
- Which test files are needed?

**Acceptance Criteria**:
- What's the definition of "done"?
- What must be tested?
- What must be documented?

**Dependencies**:
- Does this task depend on another?
- Can it be worked on independently?

**Estimated Time**:
- How long will this take?
- Is it realistic for one session?

---

## Example Task Breakdown

Given PRD for "User Authentication System":

### Parent Tasks (Submitted for Approval)

```
1.0 Implement JWT-based authentication (4 hours)
2.0 Add rate limiting and security (3 hours)
3.0 Create user management endpoints (5 hours)
4.0 Document API and test (2 hours)
```

**Then after approval**:

### Detailed Sub-Tasks

```markdown
### 1.0 Implement JWT-based authentication
- [ ] 1.1 Implement JWT token generation
  - Description: Create JWTManager class with encode/decode methods
  - Files: src/auth/jwt.py (new), tests/auth/test_jwt.py (new)
  - Tests: Test token generation, expiry, refresh
  - Dependencies: None
  - Acceptance: All tests passing, tokens properly encoded

- [ ] 1.2 Add token validation middleware
  - Description: Create middleware to validate JWT in requests
  - Files: src/middleware/auth.py (new), tests/middleware/test_auth.py (new)
  - Tests: Test valid tokens, expired tokens, missing tokens
  - Dependencies: 1.1 (JWT generation must work)
  - Acceptance: All tests passing, requests properly authenticated

- [ ] 1.3 Create password reset flow
  - Description: Implement token-based password reset
  - Files: src/auth/reset.py (new), tests/auth/test_reset.py (new)
  - Tests: Test reset token generation, validation, password update
  - Dependencies: 1.1 (JWT tokens needed for reset)
  - Acceptance: Full reset flow tested end-to-end
```

---

## Tips for Task Generation

✅ **DO**:
- Keep sub-tasks focused (one clear purpose)
- Make tasks sequential (task 1.2 depends on 1.1)
- Estimate time realistically (include testing)
- Include test requirements upfront
- List all files that will be touched
- Reference PRD sections (justify each task)

❌ **DON'T**:
- Make sub-tasks too big (shouldn't take more than 2 hours)
- Create tasks that are too small (shouldn't take less than 30 min)
- Assume context (document all assumptions)
- Forget tests (every task needs testing)
- Leave dependencies unclear (show the order)
- Overestimate time (be conservative with estimates)

---

## Using Tasks in Sessions

### AI Agent Workflow

1. **Read tasks.md** at session start
2. **Choose one sub-task** (or continue previous work)
3. **Work through acceptance criteria**
4. **Write tests** as you implement
5. **Commit code** with clear messages
6. **Update session-notes/** with what was completed
7. **Mark task complete** in tasks.md (with session link)
8. **Wait for approval** before starting next task

### Manager Review Workflow

1. **Read session-notes/YYYY-MM-DD.md**
2. **Check MANAGER SUMMARY** section
3. **Verify completed task matches** acceptance criteria in tasks.md
4. **Approve or request changes**
5. **AI continues to next task** after approval

---

## Two-Phase Approach

This workflow uses the ai-dev-tasks two-phase approach:

**Phase 1: Outline** (1-2 hours)
- Create parent tasks from PRD
- Get approval on overall approach
- Prevents wasted effort on wrong direction

**Phase 2: Implement** (actual development)
- Break into detailed sub-tasks
- Execute one sub-task per session
- Review and approve after each session

**Benefits**:
- Manager can approve overall plan before details
- Can adjust approach before starting
- Reduces risk of major rework
- Clear milestones throughout project

---

## Workflow Example

**Day 1**:
```
PRD approved → Generate Phase 1 (parent tasks only)
  → Submit for approval
```

**Day 2**:
```
Manager approves parent tasks → Generate Phase 2 (sub-tasks)
  → Begin session 1: work on 1.1
  → Session ends: Write session notes
  → Wait for approval
```

**Day 3**:
```
Manager approves session 1 → Begin session 2: work on 1.2
  → Continue...
```

---

## Managing Task Changes

**If requirements change mid-development**:

1. **Don't modify current session's tasks**
2. **Add new tasks** for new requirements
3. **Document why** (link to feedback/decision)
4. **Get approval** before working on new tasks
5. **Update tasks.md** to show changes
6. **Note in session** why scope changed

---

## Completion Criteria

Task is "done" when:
- ✅ Code written and committed
- ✅ All tests passing
- ✅ All acceptance criteria met
- ✅ Documentation updated
- ✅ Session notes completed
- ✅ Manager approved the session

---

## Next Steps

1. **Outline Parent Tasks**: From PRD, create 1.0, 2.0, 3.0, etc.
2. **Get Approval**: Manager reviews parent tasks
3. **Generate Sub-Tasks**: Break into detailed 1.1, 1.2, etc.
4. **Begin First Session**: Work on 1.1
5. **Track Progress**: Update tasks.md as tasks complete
6. **Manager Reviews**: Approve each session before continuing

---

## Related Documents

- **PRD**: See `tasks/create-prd.md` (what we're building)
- **Session Notes**: See `session-notes/_TEMPLATE.md` (how we track work)
- **Active Tasks**: See `tasks.md` (current task list)
- **CLAUDE.md**: See project context and setup
