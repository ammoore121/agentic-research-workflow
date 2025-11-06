# Project Tasks

**Status**: Active
**Last Updated**: YYYY-MM-DD
**Owner**: [Name]
**Branch**: [feature/name]

## Overview

This file uses hierarchical task numbering from [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks):
- **1.0, 2.0, 3.0** = Parent tasks (high-level milestones)
- **1.1, 1.2, 1.3** = Sub-tasks (implementation steps)
- **Status**: not started | in progress | completed | blocked
- **Sessions**: Link to session notes where task was worked on

## Workflow

1. **Planning Phase**: Parent tasks are created and approved
2. **Execution Phase**: Work on sub-tasks one per session
3. **Review Phase**: Manager approves each session (see session-notes/)
4. **Completion**: Mark tasks complete as they finish

---

## Tasks

### 0.0 Create Feature Branch
- [ ] 0.1 Create and checkout feature branch
  - **Status**: not started
  - **Session**: [Link to session notes when started]
  - **Description**: Create branch from main using naming convention: feature/[feature-name]
  - **Relevant files**: .git/config
  - **Notes**: Branch should be created before any development work begins

---

### 1.0 [Phase/Feature Name]
- [ ] 1.1 [First sub-task]
  - **Status**: not started
  - **Session**: [Link when started]
  - **Description**: What needs to be done?
  - **Relevant files**:
    - src/[file1.py](src/file1.py)
    - tests/[test_file1.py](tests/test_file1.py)
  - **Notes**: Any context or requirements?
  - **Dependencies**: Any tasks that must be done first?

- [ ] 1.2 [Second sub-task]
  - **Status**: not started
  - **Session**: [Link when started]
  - **Description**: What needs to be done?
  - **Relevant files**:
    - src/[file2.py](src/file2.py)
    - tests/[test_file2.py](tests/test_file2.py)
  - **Notes**: Any context or requirements?
  - **Dependencies**: Depends on 1.1

- [ ] 1.3 [Third sub-task]
  - **Status**: not started
  - **Session**: [Link when started]
  - **Description**: What needs to be done?
  - **Relevant files**: [List files affected]
  - **Notes**: [Any context?]
  - **Dependencies**: None

---

### 2.0 [Next Phase/Feature Name]
- [ ] 2.1 [Sub-task]
  - **Status**: not started
  - **Session**: [Link when started]
  - **Description**: What needs to be done?
  - **Relevant files**: [List files]
  - **Notes**: [Context]
  - **Dependencies**: Depends on 1.0 (all subtasks)

- [ ] 2.2 [Sub-task]
  - **Status**: not started
  - **Session**: [Link when started]
  - **Description**: What needs to be done?
  - **Relevant files**: [List files]
  - **Notes**: [Context]
  - **Dependencies**: Depends on 2.1

---

### 3.0 [Final Phase/Feature Name]
- [ ] 3.1 [Sub-task]
  - **Status**: not started
  - **Session**: [Link when started]
  - **Description**: What needs to be done?
  - **Relevant files**: [List files]
  - **Notes**: [Context]
  - **Dependencies**: Depends on 2.0 (all subtasks)

---

## Task Status Legend

| Status | Icon | Meaning | Example |
|--------|------|---------|---------|
| Not Started | `- [ ]` | Task ready but work hasn't begun | Requirements clear, no start yet |
| In Progress | `- [x]` | Currently being worked on in a session | Session 2025-11-05-1430.md |
| Completed | `- [x]` | Done and approved | Finished in Session 2025-11-04-1200.md |
| Blocked | `- [!]` | Can't proceed, waiting for decision | Waiting on manager decision re: storage backend |

**Note**: Check the corresponding session notes file to see actual status and details. This file is updated from session outcomes, not manually.

---

## How to Use This File

### For AI Agents
1. Read CLAUDE.md first (project context)
2. Read this file (what needs to be done)
3. Check latest session-notes/YYYY-MM-DD-HHmm.md (what was approved last)
4. Work on assigned sub-tasks in sequence
5. Write detailed session notes when done
6. Stop and wait for manager approval

### For Managers
1. Review session notes in `session-notes/` folder
2. Check MANAGER SUMMARY section first (what was done)
3. Check MANAGER APPROVAL section (what decisions are needed)
4. Edit approval status and add feedback
5. Save changes (syncs to team)

### For Project Updates
**When adding new tasks**:
- Use hierarchical numbering (1.0, 1.1, 1.2)
- Add description, relevant files, notes, dependencies
- Keep sub-tasks focused (one session's worth of work)
- Reference PRD (in docs/ folder) for rationale

**When tasks are completed**:
- Change `- [ ]` to `- [x]`
- Add session link (where was it completed?)
- Keep the full task description (don't delete)

---

## Progress Summary

**Total Tasks**: [Count parent tasks]
**Completed**: [Count] (X%)
**In Progress**: [Count]
**Not Started**: [Count]
**Blocked**: [Count]

**Last Session**: [session-notes/YYYY-MM-DD-HHmm.md]
**Current Focus**: [1.0 - 1.3]
**Next Review**: [When manager will review next session]

---

## Notes

- This structure is based on [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks) methodology
- Two-phase approach: Parent tasks approved first, then detailed sub-tasks executed
- Each session focuses on 1-3 sub-tasks
- Manager approval required after each session before continuing
- Links to session notes preserve context and decisions
- Archive completed milestones to keep active list focused
