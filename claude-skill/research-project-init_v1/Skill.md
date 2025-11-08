---
name: research-project-init
description: Initialize and research new business ideas, investment opportunities, data products, or agent workflows. Conducts competitive intelligence, market analysis, technical feasibility assessment, and cost/benefit analysis.

---

# Research Project Init

This skill helps initialize new research projects by conducting comprehensive competitive intelligence, market analysis, and technical feasibility assessment. It synthesizes findings into structured documentation and saves to Google Drive.

## When to Use This Skill

Trigger this skill when you want to:
- Research a new business idea
- Evaluate investment opportunities
- Assess data product viability
- Plan a new agent or workflow
- Understand a market landscape before committing resources

## Workflow

### Step 1: Gather Initial Information

Ask clarifying questions to understand the project scope:

1. **Project Description**: What's the core idea? (1-2 sentences)
2. **Hypothesis**: What are you testing or trying to prove?
3. **Benchmark/Success Criteria**: What defines success? What are you comparing against?
4. **Timeline**: How long/complex is this? (quick experiment vs. multi-month project)
5. **Budget Considerations**: Any cost constraints or target price points?

Keep the initial conversation concise. Avoid overwhelming with too many questions at once.

### Step 2: Conduct Research

See `references/research_prompts.md` for detailed research guidance. Use web search extensively to gather:

**Competitive Landscape** (5-10 competitors):
- Product descriptions and features
- Pricing models and tiers
- Strengths and weaknesses
- Target customers
- Tech stacks (if discernible)
- URLs and sources

**Market Intelligence**:
- Market size and growth trends
- Industry reports and funding activity
- White space opportunities
- Customer pain points

**Technical Feasibility**:
- Available data sources (APIs, datasets, vendors)
- Costs for data access and infrastructure
- Tech stack recommendations
- Development complexity and timeline

**Regulatory Considerations**:
- Compliance requirements
- Privacy regulations
- Legal risks
- Terms of service restrictions

**Go-to-Market Strategy**:
- Customer acquisition channels
- Pricing benchmarks
- Sales cycle insights
- User feedback on existing solutions

**Cost/Benefit Analysis**:
- One-time costs (development, setup)
- Recurring costs (infrastructure, data subscriptions)
- Break-even analysis
- Scenario planning (pessimistic, base, optimistic)

### Step 3: Synthesize Findings

See `references/document_templates.md` for detailed document structure. Create comprehensive documents that include:

- **00_PROJECT_OVERVIEW.md**: Executive summary with clear go/no-go recommendation
- **01_Research_Brief.md**: Hypothesis, questions, success criteria
- **02_Market_Landscape.md**: Competitive analysis with specific competitors and pricing
- **03_Technical_Feasibility.md**: Data sources, tech stack, costs, timeline
- **04_Go_To_Market.md**: Target customers, pricing strategy, launch plan
- **05_Risk_Assessment.md**: Legal, technical, market, financial risks
- **plan.md**: Action plan with next steps and milestones
- **CLAUDE.md**: Use the template from `assets/CLAUDE_template.md`

**Quality Standards**:
- Include specific data, not vague statements
- Cite sources with URLs
- Present tradeoffs explicitly ("If we do X, we give up Y")
- Use tables for competitive/pricing comparisons
- Provide actionable recommendations

**Document Customization**:
- Adjust depth based on project complexity
- Simple projects may only need 00, 01, and plan.md
- Adapt templates based on project type (data products vs. agent workflows vs. investments)

### Step 4: Iterate with User

After generating initial documents:

1. Present a summary of key findings
2. Highlight critical tradeoffs or decisions
3. Ask if any areas need deeper investigation
4. Incorporate user feedback
5. Refine documents based on discussion

Continue iterating until the user signals satisfaction.

### Step 5: Save to Google Drive

**Trigger Phrases**:
- "Save to Drive"
- "Save it"
- "Looks good, save"
- "Ready to save"
- "Yes, save"

When the user indicates readiness to save:

1. Confirm the project name
2. Save each document to Google Drive via the configured endpoint
3. For each document, send a POST request with:
   - `project`: Project name
   - `filename`: Document filename
   - `content`: Full markdown content
4. Confirm successful save with folder link

**How to Set Up Google Drive Integration**:

The skill needs a backend endpoint to save documents. Options:
- **Google Apps Script** (Recommended): Free, serverless, integrates with Google Drive
- **Custom API**: Your own backend service

See the main documentation for setup instructions specific to your implementation.

**Folder Structure Created**:
```
AI_Projects/{ProjectName}/
└── docs/
    ├── 00_PROJECT_OVERVIEW.md
    ├── 01_Research_Brief.md
    ├── 02_Market_Landscape.md
    ├── 03_Technical_Feasibility.md
    ├── 04_Go_To_Market.md
    ├── 05_Risk_Assessment.md
    └── plan.md
```

## Research Best Practices

### Cost/Benefit Thinking

Always present tradeoffs explicitly:
- Build vs. buy decisions
- Data quality vs. cost
- Speed vs. quality
- Complexity vs. differentiation

Create scenario analyses (pessimistic, base, optimistic) to help with decision-making.

### Search Strategy

Use multiple search queries to gather comprehensive data:
- Start broad, then narrow
- Search for competitors, pricing, and alternatives
- Look for industry reports and market sizing
- Check regulatory requirements
- Find customer reviews and pain points

Cite all sources with URLs. If information is scarce, acknowledge uncertainty rather than speculating.

### Synthesis Quality

Good research includes:
- 5-10 specific competitors with URLs
- Actual pricing data (not just "subscription model")
- Quantified market size with sources
- Specific data sources with costs
- Explicit recommendations with reasoning

Avoid generic statements. Be data-driven and actionable.

## Notes

- User prefers semi-standard folder structure (flexible at Claude's discretion)
- CLAUDE.md template is customizable - user may modify after skill execution
- Focus on cost-effectiveness and explicit tradeoff analysis
- Research should be comprehensive enough to make informed go/no-go decisions
- Documents should enable immediate execution if user decides to proceed
