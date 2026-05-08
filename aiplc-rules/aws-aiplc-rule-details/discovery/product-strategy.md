# Product Strategy

**Assume the role** of a product strategy advisor

**Phase**: DISCOVERY PHASE — Stage 3 of 4
**Conditional Phase**: Executes only for Greenfield projects, after Envision (and optionally after Prototype & Validation).

**Purpose**: Capture positioning, differentiation, and business model decisions. These are informed by the structured discovery work — validated pain points, market research, a PRFAQ that has been through stakeholder review, and optionally validated prototype feedback from real users — rather than assumptions.

## Prerequisites
- Envision stage must be complete and approved
- `aiplc-docs/discovery/discovery-document.md` must exist with Part 1 (Envision) populated
- `aiplc-docs/discovery/envision/pain-point-analysis.md` must exist
- If Prototype & Validation was executed: `aiplc-docs/discovery/prototype/validation-results.md` should exist

## Execution Steps

### Step 1: Load Prior Discovery Context

Load the following artifacts:
- `aiplc-docs/discovery/discovery-document.md` (Parts 1 & 2 if Prototype & Validation was executed, or Part 1 only if skipped)
- `aiplc-docs/discovery/envision/pain-point-analysis.md` (categorized pain points)
- `aiplc-docs/discovery/prototype/validation-results.md` (if Prototype & Validation was executed)

Use these to inform all Product Strategy decisions. Every question and recommendation should be grounded in the validated pain points, PRFAQ, and prototype feedback (if available), not assumptions.

**If Prototype & Validation was executed**: Strategy questions should reference specific validation findings (e.g., "Users validated that X is the top pain point" or "3 of 5 users requested Y"). This grounds strategy in evidence rather than assumptions.

**If Prototype & Validation was skipped**: Strategy is based on Envision findings only. Note this limitation where relevant.

### Step 2: Gather Product Strategy Inputs

Create `aiplc-docs/discovery/product-strategy/strategy-questions.md` with questions covering the areas below.

**CRITICAL — Intelligent Defaults**: Every question MUST include an intelligent default as Option A, drawn from the Envision context (pain point analysis + PRFAQ). The PM confirms or overrides rather than writing from scratch.

**MANDATORY question areas:**

#### Positioning
- How should this product be positioned in the market? (e.g., premium, budget, niche specialist, platform)
- What is the one-sentence value proposition?
- What is the primary message customers should associate with this product?

#### Differentiation
- What are the top 3 differentiators vs. existing solutions? (informed by PRFAQ competitive analysis)
- Which differentiator is the most defensible long-term?
- What is the product's unfair advantage or moat?

#### Business Model
- What is the revenue model? (subscription, one-time purchase, freemium, usage-based, marketplace, etc.)
- What is the pricing strategy? (informed by willingness-to-pay data from pain point analysis)
- What are the key cost drivers?
- What is the expected gross margin?

#### Target Market
- What is the initial beachhead market? (the specific segment to win first)
- What is the expansion path after the beachhead? (adjacent segments)
- What are the key customer acquisition channels?

#### Success Metrics
- What are the primary KPIs for the first 6 months?
- What does product-market fit look like for this product?
- What are the leading indicators of success vs. failure?

Use the standard AIPLC question format (multiple choice with [Answer]: tags, mandatory "Other" option).

```markdown
## Question [Number]
[Question text]

A) [Intelligent default from Envision context and prototype validation] ← Suggested based on your Discovery work
B) [Alternative option]
C) [Alternative option]
X) Other (please describe after [Answer]: tag below)

[Answer]: 
```

### ⛔ GATE: Await User Answers
DO NOT proceed until all strategy questions are answered and validated.
**MANDATORY**: Analyze ALL answers for ambiguities and create follow-up questions if needed.

### Step 3: Write Product Strategy to Living Document

Append Part 2 to `aiplc-docs/discovery/discovery-document.md`:

```markdown
---

# Part 2: Product Strategy

## Positioning
- **Market Position**: [Premium/Budget/Niche/Platform]
- **Value Proposition**: [One sentence]
- **Primary Message**: [What customers should associate with this product]

## Differentiation
| Differentiator | Description | Defensibility |
|---|---|---|
| [Differentiator 1] | [Description] | [High/Medium/Low] |
| [Differentiator 2] | [Description] | [High/Medium/Low] |
| [Differentiator 3] | [Description] | [High/Medium/Low] |

- **Primary Moat**: [Unfair advantage or defensible moat]

## Business Model
- **Revenue Model**: [Subscription/One-time/Freemium/Usage-based/etc.]
- **Pricing Strategy**: [Description, informed by willingness-to-pay data]
- **Key Cost Drivers**: [List]
- **Expected Gross Margin**: [Estimate]

## Target Market
- **Beachhead Market**: [Specific initial segment]
- **Expansion Path**: [Adjacent segments after beachhead]
- **Key Acquisition Channels**: [List]

## Success Metrics
| Metric | Target (6 months) | Leading Indicator |
|---|---|---|
| [KPI 1] | [Target] | [Leading indicator] |
| [KPI 2] | [Target] | [Leading indicator] |
| [KPI 3] | [Target] | [Leading indicator] |

- **Product-Market Fit Signal**: [What PMF looks like for this product]
```

Update the document status header:
```markdown
**Status**: In Progress — Envision Complete, Product Strategy Complete
```

### Step 4: Present Product Strategy Completion

```markdown
# 📊 Product Strategy Stage Complete

## Summary
- **Positioning**: [One-line summary]
- **Revenue Model**: [Model]
- **Beachhead Market**: [Segment]
- **Primary Differentiator**: [Top differentiator]

## Artifacts Updated
- `aiplc-docs/discovery/discovery-document.md` — Living document (Part 2: Product Strategy added)
- `aiplc-docs/discovery/product-strategy/strategy-questions.md` — Strategy questions with answers

## Next Step
Proceeding to **Go-to-Market** to cover marketing, sales, and launch planning.

**Please review the Product Strategy section of the Discovery Document and confirm to proceed.**
```

### ⛔ GATE: Await User Approval
DO NOT proceed to Go-to-Market until the user explicitly approves the Product Strategy output.

### Step 5: Update State Tracking

Update `aiplc-docs/aiplc-state.md`:

```markdown
## Stage Progress
### 🟣 DISCOVERY PHASE
- [x] Envision
- [x] Prototype & Validation (or skipped)
- [x] Product Strategy
- [ ] Go-to-Market
```

### Step 6: Log and Proceed

- Log completion in `aiplc-docs/audit.md`
- Proceed to Go-to-Market stage
