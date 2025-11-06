# Credits & Attribution

This project stands on the shoulders of giants. Here's a comprehensive list of what inspired and what we built upon.

---

## Primary Foundation: ai-dev-tasks

**Project**: [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks)
**Author**: [snarktank](https://github.com/snarktank)
**Stars**: 6.7k+ (as of 2025-11-05)
**License**: MIT

### What We Adopted from ai-dev-tasks

The core task management and planning methodology comes directly from ai-dev-tasks:

#### 1. Hierarchical Task Numbering
```
1.0, 2.0, 3.0     = Parent tasks (major milestones)
1.1, 1.2, 1.3     = Sub-tasks (implementation steps)
```

**Why it works**:
- Clear parent/child relationships
- Easy to reference ("work on 1.2")
- Visual hierarchy in task list
- Perfect for incremental development

#### 2. Two-Phase Task Generation

**Phase 1: Parent Tasks** (for manager approval)
- High-level milestones
- Estimated time per task
- Overall approach
- Get approval before detail work

**Phase 2: Sub-Tasks** (for execution)
- Detailed implementation steps
- Acceptance criteria
- File modifications needed
- Dependencies between tasks

**Why it works**:
- Prevents wasted effort on wrong direction
- Manager can adjust approach early
- Clear visibility into project scope
- Reduces cascading rework

#### 3. PRD Template Structure

Nine core sections for requirements:
1. Overview
2. Goals (measurable)
3. User Stories
4. Functional Requirements
5. Non-Goals
6. Design Considerations
7. Technical Considerations
8. Success Metrics
9. Open Questions

**Why it works**:
- Comprehensive but not overwhelming
- Separates requirements from design
- Clear scope definition
- Easy to reference during implementation

#### 4. Clarifying Questions Framework

Using A/B/C/D option format:
```
1. Project Scope?
   A. Small (1-2 weeks)
   B. Medium (2-4 weeks)
   C. Large (4-8 weeks)
   D. Other

2. Primary Goal?
   A. Improve performance
   B. Add capability
   C. Fix problem
   D. Reduce cost
```

**Why it works**:
- Structured prompts reduce ambiguity
- User responds with simple codes (1A, 2B, 3C)
- Minimal back-and-forth
- AI has clear context for next steps

#### 5. Incremental Execution Model

Work one sub-task at a time:
- Stop after each task
- Human verifies
- Continue to next task
- Prevents cascading errors

**Why it works**:
- Easy to adjust course
- Clear progress checkpoints
- Failures are isolated
- Better quality control

---

## Our Additions to ai-dev-tasks

We extended ai-dev-tasks with capabilities for AI-assisted web development:

### 1. Research Automation

**Added**: Comprehensive research phase before planning

What we built:
- Claude Skill for automated research
- Competitive analysis automation
- Market sizing and trends research
- Technical feasibility assessment
- Go-to-market strategy development
- Risk assessment framework

**Why added**:
- ai-dev-tasks assumes PRD exists
- We go one step back: create PRD from research
- Ensures decisions are data-driven
- Reduces guesswork in planning

### 2. Session-Based Development

**Added**: Structured development sessions with automatic context management

What we built:
- Automatic context loading (CLAUDE.md, tasks.md, previous sessions)
- Standardized session notes format
- Clear checkpoint triggers (time, tasks, blockers)
- Documentation of decisions and rationale

**Why added**:
- AI needs consistent context reloading
- Prevents context loss between sessions
- Enables AI autonomy with human oversight
- Creates audit trail of decisions

### 3. Manager Approval Workflow

**Added**: Clear feedback loop between AI development and manager oversight

What we built:
- Unified session notes with approval section at top
- Manager approval status options:
  - APPROVED (continue)
  - APPROVED WITH TASKS (add work)
  - CHANGES NEEDED (redo)
  - ROLLBACK (revert to commit)
  - PAUSED (hold work)
- Mobile-friendly review via Google Drive
- Automatic sync of approvals back to AI

**Why added**:
- ai-dev-tasks doesn't include manager oversight
- Need human-in-the-loop for direction decisions
- Manager needs to approve before continuing
- Prevents runaway AI work in wrong direction

### 4. Google Drive Integration

**Added**: Seamless manager oversight without special permissions

What we built:
- Google Drive Desktop sync for session-notes
- Manager reviews and approves on phone
- No MCP write access needed
- Automatic bidirectional sync

**Why added**:
- Managers work on phones
- GitHub is good for code, bad for phone review
- Google Drive is good for phone, good for sync
- No special tooling needed

### 5. Research → PRD → Tasks → Code Traceability

**Added**: Complete linkage from initial research to final code

What we built:
- Research docs stored in GitHub /docs/
- PRD links to research sources
- Tasks reference PRD requirements
- Session notes document decisions
- Code commits reference task numbers
- Full audit trail preserved

**Why added**:
- ai-dev-tasks doesn't address research phase
- Need clear traceability for decision-making
- Useful for onboarding new team members
- Important for post-mortems and improvements

### 6. Unified Session Notes Format

**Added**: Single session file with three sections

What we built:
- MANAGER APPROVAL section (at top, with date input)
- MANAGER SUMMARY section (concise, 5-10 min read)
- DETAILED NOTES section (full AI context)

**Why added**:
- ai-dev-tasks uses separate files for different purposes
- Unified file prevents information scattering
- Manager approval is immediately visible
- AI and manager context in one place

---

## Technical Stack & Dependencies

### Development Tools

- **Claude AI** - Language model for all AI tasks
- **Claude Skills** - Framework for specialized workflows
- **GitHub** - Version control and code hosting
- **Google Drive Desktop** - File sync for approval workflow
- **Git** - Local version control

### Methodologies & Frameworks

- **ai-dev-tasks** - Task management and planning
- **Hierarchical task numbering** - From ai-dev-tasks
- **PRD template structure** - From ai-dev-tasks
- **Two-phase generation** - From ai-dev-tasks

### Documentation & Writing

- **Markdown** - All documentation format
- **GitHub Flavored Markdown** - GitHub-specific features
- **Plain text** - Maximum portability

---

## Key Insights Borrowed

### From ai-dev-tasks

1. **Simplicity wins** (4 files, maximum impact)
   - We kept this principle
   - Clean folder structure, clear files

2. **Templates are prompts**
   - PRD/task generation templates are AI prompts
   - Not just instructions, but actual prompts

3. **Pause points prevent errors**
   - Review after each major phase
   - Approval gates reduce rework

4. **Context is everything**
   - More context = better output
   - Reference previous artifacts

5. **Target audience clarity**
   - Write for juniors (explicit, detailed)
   - We write for AI (even more explicit)

### From Development Best Practices

1. **Version control everything**
   - All decisions documented in Git
   - Full history preserved

2. **Automation + Human Oversight**
   - AI handles implementation
   - Manager provides direction

3. **Mobile-first for managers**
   - Approval workflow on phone
   - Google Drive accessibility

4. **Clear approval workflow**
   - Manager knows what to decide
   - Options pre-defined
   - Easy to track status

---

## Why We Built This

**Problem**:
- Existing AI development tools lack structure
- No clear process from idea to product
- Missing research automation
- Unclear manager oversight

**Solution**:
- Combine ai-dev-tasks structure with research automation
- Add session-based development for AI continuity
- Build manager oversight without heavy tools
- Create end-to-end workflow from idea to code

**Result**:
- Complete system for AI-assisted web development
- Clear roles for AI agent and manager
- Documented decision-making process
- Ready-to-use templates and examples

---

## Open Source Philosophy

This project is open source (MIT License) because:

1. **ai-dev-tasks is open** - We respect their openness
2. **Community benefits** - Others can improve and share
3. **Transparency matters** - Open code builds trust
4. **Everyone should build** - Barrier to entry should be low

We encourage:
- Forking and customizing for your needs
- Sharing improvements and variations
- Crediting sources (as we do here)
- Contributing back improvements

---

## Inspiration & Influences

### AI Development Workflows
- Inspired by autonomous agent concepts
- Influenced by human-in-the-loop AI systems
- Shaped by real experience using Claude for development

### Product Management
- Influenced by Lean Product Development
- Shaped by experience with PRDs and requirements
- Learned from product-engineer collaboration

### Project Management
- Inspired by Agile methodologies
- Shaped by incremental development practices
- Learned from iterative approval processes

### Developer Experience
- Informed by Git and GitHub workflows
- Shaped by documentation practices
- Influenced by developer tool design

---

## To Our Foundations

**To snarktank and the ai-dev-tasks project**:
Thank you for creating a simple, elegant task management methodology. Your work clearly and thoughtfully shows how to break projects into deliverable chunks. We've built this extended workflow on your solid foundation.

**To the Claude team**:
Your AI capabilities made this workflow possible. The ability for Claude to maintain context, write code, understand requirements, and follow structured processes enables the entire agentic approach.

**To the open source community**:
Your work, documentation, and shared knowledge made this project possible. From git to markdown to the open internet, we stand on shoulders of thousands.

---

## License & Reuse

This project is MIT licensed. You can:
- ✅ Use it commercially
- ✅ Modify it
- ✅ Distribute it
- ✅ Use it privately
- ✅ Include it in your projects

We only ask that you:
- Include the license file
- Credit the original authors (us and our foundations)
- Don't hold us liable if something breaks

See [LICENSE](../LICENSE) file for full terms.

---

## Contributing

Found something awesome we missed?

1. Fork the repository
2. Create a branch for your improvement
3. Make your changes
4. Create a pull request
5. We'll review and merge!

Or start your own variation! Open source is about sharing and improving together.

---

## Questions About Attribution?

If you're unsure about attribution or have questions:

1. **Check this file** - Most common questions answered here
2. **Review ai-dev-tasks** - See original methodology: https://github.com/snarktank/ai-dev-tasks
3. **Ask Claude** - Upload repo and ask about any specific component
4. **Open an issue** - We'll clarify

---

**Last Updated**: November 2025
**Based On**: ai-dev-tasks by snarktank
**Extended With**: Research automation, session management, manager approval
**License**: MIT

---

Thank you to everyone who helped make this possible. Standing on the shoulders of giants, indeed.
