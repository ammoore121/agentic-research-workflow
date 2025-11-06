# [Project Name]

## Metadata

GitHub: owner/repo-handle
Status: [Research | In Development | Active | Maintenance]
Owner: [Name] (@github-handle)
Last Updated: YYYY-MM-DD

Strategic Docs: https://drive.google.com/drive/folders/[FOLDER_ID]
- Market Analysis: [Link to 02_Market_Landscape.md]
- MVP Spec: [Link to 03_MVP_Spec.md]
- Technical Feasibility: [Link to 04_Technical_Feasibility.md]
- Risk Assessment: [Link to 05_Risk_Assessment.md]
- Plan: [Link to plan.md]

---

## Project Summary

[1-2 sentences describing what this project is, the problem it solves, and who it's for]

---

## Development Setup

Language: [Python 3.12 | Node.js 18+ | Go 1.21+ | etc.]
Package Manager: [pip | npm | uv | cargo]

Quick Start:
```bash
git clone https://github.com/[owner]/[repo]
cd [repo]
python -m venv venv && source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -e ".[dev]"
pytest  # Verify setup works
```

---

## Development Commands

Test: pytest [tests/]
Lint: ruff check src/
Format: black src/
Types: mypy src/
Run: [project-specific command]
Build: [build command if applicable]

---

## Code Standards

Naming: snake_case (functions/variables), PascalCase (classes), UPPER_SNAKE_CASE (constants)
Line length: 100 characters maximum
Type annotations: Required for all public functions
Docstrings: Google-style format for modules, classes, and public functions
Imports: stdlib → third-party → local (blank lines between groups)
Testing: All public functions should have tests in tests/

---

## Architecture

Directory Structure:
src/
  models/         Data structures and schemas
  services/       Business logic and external integrations
  utils/          Helper functions and utilities
  main.py         Entry point
tests/            Test files, mirror src/ structure
docs/             Technical documentation
session-notes/    Development session logs (AI-generated)

Key Components:
- [Component Name]: Brief description, key files, dependencies
- [Component Name]: Brief description, key files, dependencies

---

## For AI Agents

Session Startup: Read tasks.md, latest 2 session-notes/, and this CLAUDE.md
Workflow: Work on task → implement → test → commit → update session-notes/
Checkpoint Triggers: (1) 90 min elapsed, (2) 3-5 tasks complete, (3) major architectural change, (4) blocker encountered, (5) unclear approach

Session Output:
- Git commits with descriptive messages
- session-notes/YYYY-MM-DD-HHmm.md summarizing: completed tasks, code changes, decisions made, blockers
- tasks.md updated with completed tasks, in-progress tasks, blockers

When Implementing:
1. Check strategic docs (links in Metadata) for architecture decisions and requirements
2. Follow code standards above for consistency
3. Write tests for new code (run pytest before completing task)
4. Update tasks.md with progress and any blockers
5. At checkpoint, review session progress and generate session note
6. If uncertain about approach, reference strategic docs and ask clarifying questions

---

## Dependencies

[dependency-name]    Why: Brief reason (e.g., "API requests", "database ORM")
[dependency-name]    Why: Brief reason
[dependency-name]    Why: Brief reason

Dev Dependencies:
pytest               Testing framework
pytest-cov           Code coverage
black                Code formatting
ruff                 Linting
mypy                 Static type checking

---

## Common Issues

Issue: [Problem description]
Solution: [Step-by-step fix]

Issue: [Problem description]
Solution: [Step-by-step fix]

---

## Notes

Strategic decisions are documented in Google Drive (links above) - reference these when making architectural choices or deciding between approaches.

This project uses semi-autonomous AI development with human check-ins. See "For AI Agents" section above for workflow details.
