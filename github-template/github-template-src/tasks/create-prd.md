# Create Product Requirements Document (PRD)

**Based on**: [ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks) methodology, adapted for research + development workflow

## What This Does

This prompt guides creating a comprehensive PRD from research findings and project goals. The PRD becomes the foundation for task generation and feature implementation.

## When to Use

- Starting a new feature (after research-project-init skill completes research)
- Planning a significant project phase
- Clarifying requirements before development begins
- Documenting project scope and success criteria

---

## PRD Generation Workflow

### Phase 1: Ask Clarifying Questions

Before generating the full PRD, ask 3-5 essential questions to understand scope:

**Format**: Use A/B/C/D options to streamline responses

```
I have some clarifying questions to ensure the PRD is accurate and complete.

1. **Project Scope**
   A. Small feature (1-2 weeks of development)
   B. Medium feature (2-4 weeks of development)
   C. Large feature (4-8 weeks of development)
   D. Other (describe): ___________

2. **Primary Goal**
   A. Improve user experience / speed
   B. Add new capability / feature
   C. Fix existing problem / bug
   D. Reduce cost / infrastructure
   E. Other: ___________

3. **Success Metric** (How will we know this succeeded?)
   A. User adoption rate ____%
   B. Performance improvement (specific metric)
   C. Customer feedback / satisfaction
   D. Cost savings $ or %
   E. Other: ___________

4. **Timeline Flexibility**
   A. Hard deadline (must ship by YYYY-MM-DD)
   B. Soft deadline (target ship but flexible)
   C. No deadline (whenever ready is fine)

5. **Dependencies**
   A. Standalone (no other features needed first)
   B. Depends on: ___________
   C. Other projects depend on this: ___________

**Respond with**: 1A, 2B, 3D, etc.
```

**User responds with**: Simple answer like "1B, 2A, 3A-15%, 4B, 5A"

### Phase 2: Generate Full PRD (After Approval)

Once you receive responses, generate complete PRD using structure below.

---

## PRD Template

**Status**: DRAFT (pending approval)
**Created**: YYYY-MM-DD
**Owner**: [Manager/PM name]
**Project**: [Project name]
**Epic**: [Parent epic, if applicable]

### 1. Overview
**1-2 sentence summary**: What is this feature? What problem does it solve?

**User Impact**: How does this improve things for users?

**Business Impact**: What's the business benefit?

**Related Research**:
- [Link to research docs if applicable]
- [Competitive analysis findings]
- [Market sizing data]

### 2. Goals (Measurable)

What are we trying to accomplish? Make goals SMART (Specific, Measurable, Achievable, Relevant, Time-bound).

- **Goal 1**: [Specific, measurable goal] by [date/condition]
  - Metric: How we'll measure success
  - Target: [Specific target number]

- **Goal 2**: [Specific, measurable goal]
  - Metric: How we'll measure success
  - Target: [Specific target number]

- **Goal 3**: ...

### 3. User Stories

What user problems are we solving? Format: "As a [user type], I want [action], so that [benefit]"

- **Story 1**: As a [user], I want [action], so that [benefit]
  - Context: Why this matters
  - Acceptance criteria:
    - [ ] Criterion 1
    - [ ] Criterion 2
    - [ ] Criterion 3

- **Story 2**: As a [user], I want [action], so that [benefit]
  - Context: Why this matters
  - Acceptance criteria:
    - [ ] Criterion 1
    - [ ] Criterion 2

### 4. Functional Requirements

What does the system need to DO?

**4.1 Feature Set**
- Requirement 1: [Description]
  - Scope: [What's included]
  - Out of scope: [What's NOT included]
  - Priority: Must-have / Nice-to-have

- Requirement 2: [Description]
  - Scope: [What's included]
  - Out of scope: [What's NOT included]
  - Priority: Must-have / Nice-to-have

**4.2 Integration Points**
- [System A] integration: [What needs to connect]
- [System B] integration: [What needs to connect]
- External APIs: [Any external services]

**4.3 Data Requirements**
- Data input: [What data comes in]
- Data storage: [Where data is stored]
- Data output: [What data comes out]

### 5. Non-Goals

What are we explicitly NOT doing? Why?

- Non-goal 1: [What we're not doing and why]
  - Reason: [Why this is out of scope]
  - Future: [Might be in future release?]

- Non-goal 2: [What we're not doing and why]
  - Reason: [Why this is out of scope]

### 6. Design Considerations

Decisions about HOW the feature works (not implementation details):

**6.1 User Experience**
- How will users interact with this feature?
- What's the mental model? (How do users think about it?)
- Any special UX patterns?

**6.2 Usability**
- Accessibility requirements (WCAG, mobile, etc.)
- Keyboard shortcuts / commands?
- Internationalization needs?

**6.3 Constraints**
- Browser/device support?
- Performance targets? (response time, throughput)
- Scalability targets? (concurrent users, data size)

### 7. Technical Considerations

What implementation approaches exist? What are the tradeoffs?

**7.1 Architecture Options**
- **Option A**: [Description]
  - Pros: [Benefits]
  - Cons: [Drawbacks]
  - Estimated effort: [Time to implement]
  - Tech stack: [Technologies needed]

- **Option B**: [Description]
  - Pros: [Benefits]
  - Cons: [Drawbacks]
  - Estimated effort: [Time to implement]
  - Tech stack: [Technologies needed]

**7.2 Recommended Approach**
- **Chosen**: Option [A/B]
- **Reasoning**: Why this approach?
- **Risk mitigations**: What could go wrong and how to handle it?

**7.3 Technical Dependencies**
- Infrastructure requirements: [What infrastructure is needed?]
- Data sources: [Any databases, APIs, external data?]
- Libraries / frameworks: [Specific tech needed?]
- Cost implications: [Any cost impacts?]

### 8. Success Metrics

How will we know this shipped successfully?

| Metric | Baseline | Target | Timeline |
|--------|----------|--------|----------|
| [Metric 1] | [Current value] | [Target value] | [When measured] |
| [Metric 2] | [Current value] | [Target value] | [When measured] |
| [Metric 3] | [Current value] | [Target value] | [When measured] |

### 9. Open Questions

Questions that need answering before implementation starts:

- **Question 1**: [What's unclear?]
  - Impact: [How does this affect the project?]
  - Owner: [Who should answer this?]
  - Timeline: [When do we need the answer?]

- **Question 2**: [What's unclear?]
  - Impact: [How does this affect the project?]
  - Owner: [Who should answer this?]
  - Timeline: [When do we need the answer?]

### 10. Research Sources
**[NEW - Research Integration]**

Where did the information in this PRD come from?

**Market Research**:
- [Link to market analysis]
- [Link to competitive analysis]
- [Link to customer feedback]

**Technical Feasibility**:
- [Link to tech assessment]
- [Link to cost analysis]
- [Link to vendor options]

**Internal**:
- [Link to prior art / similar features]
- [Link to architecture docs]

### 11. Session Plan
**[NEW - Session Integration]**

How will this be implemented across sessions?

**Phase 1**: [Description] - Est. X hours
- Tasks: 1.0, 1.1, 1.2
- Deliverable: [What gets completed]

**Phase 2**: [Description] - Est. X hours
- Tasks: 2.0, 2.1, 2.2
- Deliverable: [What gets completed]

**Phase 3**: [Description] - Est. X hours
- Tasks: 3.0, 3.1, 3.2
- Deliverable: [What gets completed]

**Estimated Total**: X hours across Y sessions

**Implementation Blockers**: [Any decisions needed before work can start?]

### 12. Approval Status
**[NEW - Approval Workflow]**

**Status**: DRAFT | UNDER REVIEW | APPROVED | REVISION REQUESTED

**Created**: YYYY-MM-DD
**Last Updated**: YYYY-MM-DD
**Reviewed By**: [Manager name]
**Approved On**: YYYY-MM-DD

**Approval Notes**:
```
[Manager's approval notes, feedback, or revision requests]
```

### 13. Manager Notes
**[NEW - Feedback Section]**

Any additional context or notes from the project manager:

```
[Additional context, concerns, strategic notes]
```

---

## Creating the PRD

### Instructions

1. **Ask Clarifying Questions** (send questions to user/manager)
   - Wait for responses in format "1A, 2B, 3C, etc."

2. **Generate Full PRD** (after approval)
   - Fill in all 13 sections above
   - Make it specific and detailed
   - Reference research where applicable
   - Include phase breakdowns for implementation

3. **Share for Approval**
   - Present PRD to manager/stakeholder
   - Highlight key decisions
   - Ask for approval before proceeding to task generation

4. **Next Step**: Once approved, use `generate-tasks.md` to break into implementation tasks

---

## Tips for Good PRDs

✅ **DO**:
- Be specific (use numbers, dates, concrete examples)
- Include tradeoffs (if we do X, we give up Y)
- Link to research (why are we doing this?)
- Make goals measurable (not "make it faster" but "reduce load time from 2s to 500ms")
- Consider both implementation effort AND impact
- Anticipate questions and answer them upfront

❌ **DON'T**:
- Leave it vague ("improve user experience" without specifics)
- Make unquantified claims ("increase adoption")
- Include implementation details (that's for task generation)
- Forget about non-goals (what are we NOT doing?)
- Ignore technical constraints (infrastructure, cost, etc.)
- Skip the success metrics (how will you know this worked?)

---

## Example PRD Structure

For a real example, check a previous project's PRD in `docs/` folder, or create your first one using this template.

---

## Next Steps

1. **Get Approval**: Manager reviews and approves PRD
2. **Generate Tasks**: Use `tasks/generate-tasks.md` to create detailed task list
3. **Begin Development**: Work through tasks in sessions per session-notes/ workflow
4. **Track Progress**: Update `tasks.md` as sessions complete
5. **Session Reviews**: Manager reviews session-notes and approves/provides feedback
