# Document Templates & Structure

This guide explains the structure and purpose of each document generated during research project initialization.

## Document Overview

All documents should be created in Google Drive at: `AI_Projects/{ProjectName}/`

| Document | Purpose | Length | Who Reads |
|----------|---------|--------|-----------|
| 00_PROJECT_OVERVIEW.md | Executive summary & go/no-go decision | 2-3 pages | Decision maker, investor, team lead |
| 01_Research_Brief.md | Research hypothesis, questions, methodology | 1-2 pages | Project team, future reference |
| 02_Market_Landscape.md | Competitive analysis, market size, opportunities | 4-8 pages | Team, stakeholders, planning |
| 03_Technical_Feasibility.md | Data sources, tech stack, costs, timeline | 3-5 pages | Technical team, budgeting |
| 04_Go_To_Market.md | Customer acquisition, pricing, launch strategy | 2-4 pages | Product, sales, marketing teams |
| 05_Risk_Assessment.md | Legal, technical, market, financial risks | 2-3 pages | Decision maker, compliance |
| plan.md | Action plan, milestones, next steps | 1-2 pages | All stakeholders |
| CLAUDE.md | AI context for coding phases | ~0.5 pages | AI agents (Claude Code) |

## Template: 00_PROJECT_OVERVIEW.md

```markdown
# Project: [Project Name]

**Project Status:** Research Phase
**Date Initiated:** YYYY-MM-DD
**Last Updated:** YYYY-MM-DD

## The Opportunity

[2-3 sentence summary of the core idea and why it matters]

Example: "Build a specialized data platform for litigation finance investors to predict case outcomes using public court records and ML. Currently investors rely on manual research; a data-driven alternative could capture 5-10% of the $17B market."

## Key Findings

### Market Opportunity
- Market Size: $[X]B globally, growing [Y]% CAGR
- Target Customer: [Specific segment with size estimate]
- Market Gap: [Clear unmet need identified in research]

### Competitive Position
- Direct Competitors: [X] (list top 3)
- Differentiation: [Specific advantage vs competitors]
- Go-to-Market: [Primary customer acquisition approach]

### Technical Viability
- Feasibility: [High/Medium/Low] - [Brief reasoning]
- Key Data Source: [Primary data input]
- Development Timeline: [X weeks/months for MVP]
- Initial Cost Estimate: $[X] for MVP development, $[Y]/month recurring

### Key Risks
- [Risk 1]: [Impact] - [Mitigation]
- [Risk 2]: [Impact] - [Mitigation]

## Recommendation

### RECOMMENDATION: [GO / NO-GO / CONDITIONAL]

[1-2 sentence explanation of recommendation]

**Confidence Level:** [High/Medium/Low]

**If GO:**
- Next immediate steps
- Timeline to first MVP
- Budget required

**If NO:**
- Key blocker(s)
- What would change the recommendation
- Alternative approaches to consider

## Details

For detailed analysis, see:
- Market Landscape: `02_Market_Landscape.md`
- Technical Details: `03_Technical_Feasibility.md`
- Implementation Plan: `plan.md`
```

## Template: 01_Research_Brief.md

```markdown
# Research Brief: [Project Name]

**Research Conducted By:** [Your name]
**Date:** YYYY-MM-DD
**Status:** [In Progress / Complete]

## Hypothesis

What are we testing?

[Clearly state the core assumption or question]

Example: "We hypothesize that litigation finance investors will pay for a data platform that predicts case outcomes with >80% accuracy and covers 80%+ of active US litigation."

## Research Questions

What do we need to answer to validate the hypothesis?

1. [Question 1]?
2. [Question 2]?
3. [Question 3]?
4. [Question 4]?

## Success Criteria

How will we know if this is worth pursuing?

- [ ] Market size > $[X]B
- [ ] [X]+ identifiable competitors to learn from
- [ ] Total development cost < $[X]K
- [ ] [Other metric specific to your project]

## Research Scope

What are we researching?

- Competitive landscape: [Scope]
- Market sizing: [Scope]
- Technical feasibility: [Scope]
- Regulatory requirements: [Scope]
- GTM strategy: [Scope]

## Key Assumptions

What are we assuming to be true?

1. [Assumption 1 - evidence/risk]
2. [Assumption 2 - evidence/risk]
3. [Assumption 3 - evidence/risk]

## Timeline & Complexity

- **Estimated Research Duration:** [X hours]
- **Project Complexity:** [Low / Medium / High]
- **Key Unknowns:** [List factors that create uncertainty]

## Methodology

How are we conducting the research?

- Web search for competitors, pricing, reviews
- Industry analyst reports (Gartner, IDC, etc.)
- Government/regulatory databases
- Customer feedback analysis
- Technical feasibility research
```

## Template: 02_Market_Landscape.md

```markdown
# Market Landscape: [Project Name]

**Date:** YYYY-MM-DD
**Market:** [Market name]
**Focus:** [Geographic scope, customer segment, etc.]

## Market Overview

### Size & Growth
- **Total Addressable Market (TAM):** $[X]B (Source: [Report], [Year])
- **Current Market Size:** $[X]B
- **Growth Rate:** [X]% CAGR through [Year]
- **Key Drivers:** [What's driving growth]

### Market Segments
| Segment | Size | Growth | Notes |
|---------|------|--------|-------|
| [Segment 1] | $[X]M | [X]% | [Details] |
| [Segment 2] | $[X]M | [X]% | [Details] |
| [Segment 3] | $[X]M | [X]% | [Details] |

## Competitive Landscape

### Market Leaders

#### 1. [Competitor Name]
- **URL:** [Website]
- **Founded:** [Year]
- **Funding:** $[X] (if startup)
- **Pricing:** [Tiers and costs]
- **Primary Features:** [Key features]
- **Target Customers:** [Who they serve]
- **Strengths:** [Competitive advantages]
- **Weaknesses:** [Gaps or limitations]

#### 2-10. [Other competitors]

### Competitive Matrix

| Feature | [Our Project] | [Competitor 1] | [Competitor 2] | [Competitor 3] |
|---------|---------------|----------------|----------------|----------------|
| [Feature 1] | [ ] | [ ] | [ ] | [ ] |
| [Feature 2] | [ ] | [ ] | [ ] | [ ] |
| [Pricing] | | | | |

## Market Opportunities & Gaps

### White Space Identified
1. [Opportunity 1]: Why competitors don't serve this
2. [Opportunity 2]: Unmet customer need
3. [Opportunity 3]: Emerging market trend

### Customer Pain Points
- [Pain point 1]: Severity [High/Med/Low]
- [Pain point 2]: Severity [High/Med/Low]

### Recommended Positioning
Our project should focus on [specific differentiation] to capture [target segment].

## Trends & Market Drivers

- [Trend 1]: [Direction and impact]
- [Trend 2]: [Direction and impact]
- [Trend 3]: [Direction and impact]

## Customer Segments

| Segment | Size | Growth | Key Needs |
|---------|------|--------|-----------|
| [Segment 1] | [X]K customers | [X]% | [Needs] |
| [Segment 2] | [X]K customers | [X]% | [Needs] |

## Pricing Intelligence

**Market Pricing Ranges:**
- [Tier 1]: $[X]/month for [value prop]
- [Tier 2]: $[X]/month for [value prop]
- [Tier 3]: $[X]/month for [value prop]

**Benchmark Recommendation:** Position at $[X]/month for [segment]

## Sources

- [Source 1]: [URL] ([Date])
- [Source 2]: [URL] ([Date])
```

## Template: 03_Technical_Feasibility.md

```markdown
# Technical Feasibility: [Project Name]

**Date:** YYYY-MM-DD
**Assessed By:** [Your name]
**Complexity Level:** [Low / Medium / High]

## Tech Stack Recommendation

### Core Technologies
- **Language:** [Python / Node.js / Go / etc.]
- **Framework:** [Django / FastAPI / Express / etc.]
- **Database:** [PostgreSQL / MongoDB / etc.]
- **Hosting:** [AWS / GCP / Heroku / etc.]
- **Frontend:** [React / Vue / etc.] (if applicable)

### Rationale
Why this stack is appropriate for this project and market position.

## Data Sources & Costs

### Primary Data Source
- **Name:** [Data source]
- **Type:** [API / Dataset / Service]
- **Coverage:** [What's included]
- **Quality:** [Reliability assessment]
- **Cost:** $[X]/month
- **Update Frequency:** [Real-time / Daily / Weekly]
- **Documentation:** [Quality assessment]

### Secondary Data Sources
| Source | Cost | Quality | Coverage |
|--------|------|---------|----------|
| [Source 1] | $[X]/mo | [Low/Med/High] | [Details] |
| [Source 2] | $[X]/mo | [Low/Med/High] | [Details] |

**Total Data Costs:** $[X]-[Y]/month

## Infrastructure & Hosting Costs

| Component | Cost | Notes |
|-----------|------|-------|
| Compute (servers) | $[X]/mo | [Size estimate] |
| Database | $[X]/mo | [Storage estimate] |
| Data storage | $[X]/mo | [Estimate] |
| Analytics/monitoring | $[X]/mo | [Tools] |
| **Total Recurring** | **$[X]/mo** | **[For X users]** |

## Development Costs

### MVP Development
- **Estimated Effort:** [X] person-weeks
- **Team Size:** [X] engineers
- **Duration:** [X] weeks calendar time
- **Cost (internal):** $[X]K (based on [rate])

### Implementation Timeline
- Week 1-2: [Phase 1]
- Week 3-4: [Phase 2]
- Week 5-6: [Phase 3]
- Week 7: [Testing & launch]

## Technical Risks & Mitigations

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|-----------|
| [Risk 1] | [High/Med/Low] | [High/Med/Low] | [Plan] |
| [Risk 2] | [High/Med/Low] | [High/Med/Low] | [Plan] |

## Scalability Considerations

- **Initial Scale Target:** [X] users
- **Scaling Timeline:** [When scale matters]
- **Scaling Cost Impact:** [Expected cost increase]
- **Architectural Implications:** [What changes needed]

## Vendor/Third-Party Dependencies

- [Vendor 1]: [What they provide] - [Risk level]
- [Vendor 2]: [What they provide] - [Risk level]
```

## Template: plan.md

```markdown
# Project Plan: [Project Name]

**Status:** [Planning / Ready to Execute / In Progress]
**Last Updated:** YYYY-MM-DD

## Goal

[Clear statement of what we're building and why]

## Phases

### Phase 1: [Phase Name]
**Duration:** [Weeks]
**Goals:**
- [Goal 1]
- [Goal 2]
- [Goal 3]

**Deliverables:**
- [Deliverable 1]
- [Deliverable 2]

### Phase 2: [Phase Name]
[Repeat structure]

## Success Metrics

How we'll know this succeeded:

- [Metric 1]: [Target]
- [Metric 2]: [Target]
- [Metric 3]: [Target]

## Resources Required

- **Team:** [X] engineers, [other roles]
- **Budget:** $[X]K total, $[Y]K/month recurring
- **Timeline:** [X] months to first customer

## Key Milestones

- [Date/Week]: [Milestone 1]
- [Date/Week]: [Milestone 2]
- [Date/Week]: [Milestone 3]

## Next Steps

1. [Immediate action]
2. [Next action]
3. [Following action]
```

## Customization by Project Type

### For Data Products
- Emphasize: Data sources, update frequency, data quality metrics
- De-emphasize: UI/UX design
- Focus: Data accuracy, coverage, completeness

### For Software/Platforms
- Emphasize: User experience, feature set, scalability
- De-emphasize: Raw market size (focus on TAM you can capture)
- Focus: Product roadmap, user acquisition

### For Investment Opportunities
- Emphasize: Market timing, financial projections, risk factors
- De-emphasize: Technical details
- Focus: ROI analysis, scenario planning, competitive positioning

### For Agent Workflows
- Emphasize: Integration points, training data, accuracy metrics
- De-emphasize: Traditional market size (focus on productivity gains)
- Focus: Use cases, accuracy rates, implementation complexity
