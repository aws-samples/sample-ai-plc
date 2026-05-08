# Go-to-Market

**Assume the role** of a go-to-market strategist

**Phase**: DISCOVERY PHASE — Stage 4 of 4
**Conditional Phase**: Executes only for Greenfield projects, after Product Strategy.

**Purpose**: Cover marketing, sales, and launch planning before Construction begins. This is the final stage of Discovery — completing the single living document that Inception consumes as input context.

## Prerequisites
- Envision stage must be complete and approved
- Product Strategy stage must be complete and approved
- `aiplc-docs/discovery/discovery-document.md` must exist with prior parts populated (Envision, optionally Prototype & Validation, Product Strategy)

## Execution Steps

### Step 1: Load Prior Discovery Context

Load the following artifacts:
- `aiplc-docs/discovery/discovery-document.md` (All prior parts: Envision, Prototype & Validation if executed, Product Strategy)
- `aiplc-docs/discovery/envision/pain-point-analysis.md` (categorized pain points)
- `aiplc-docs/discovery/prototype/validation-results.md` (if Prototype & Validation was executed)

Use these to inform all Go-to-Market decisions. Every recommendation should be grounded in the validated pain points, PRFAQ, prototype feedback (if available), and product strategy — not assumptions.

### Step 2: Gather Go-to-Market Inputs

Create `aiplc-docs/discovery/go-to-market/gtm-questions.md` with questions covering the areas below.

**CRITICAL — Intelligent Defaults**: Every question MUST include an intelligent default as Option A, drawn from the Envision and Product Strategy context. The PM confirms or overrides rather than writing from scratch.

**MANDATORY question areas:**

#### Marketing Strategy
- What is the primary marketing channel for reaching the beachhead market?
- What is the messaging framework? (key messages, tagline, elevator pitch)
- What content or assets are needed for launch? (landing page, demo, case study, etc.)
- What is the pre-launch awareness strategy?

#### Sales Approach
- What is the sales model? (self-serve, inside sales, field sales, partner/channel, PLG)
- What is the expected sales cycle length?
- What are the key objections prospects will raise, and how do we address them?
- What sales enablement materials are needed?

#### Launch Planning
- What is the target launch date? (informed by PRFAQ summary paragraph)
- What is the launch strategy? (big bang, soft launch, beta/early access, phased rollout)
- What are the launch milestones and dependencies?
- What is the MVP scope for launch vs. post-launch roadmap?

#### Success Metrics & Monitoring
- What are the launch success criteria? (first 30/60/90 days)
- What metrics will be tracked from day one?
- What is the feedback collection mechanism post-launch?
- What are the kill criteria? (conditions under which to pivot or stop)

Use the standard AIPLC question format (multiple choice with [Answer]: tags, mandatory "Other" option).

```markdown
## Question [Number]
[Question text]

A) [Intelligent default from Discovery context] ← Suggested based on your Discovery work
B) [Alternative option]
C) [Alternative option]
X) Other (please describe after [Answer]: tag below)

[Answer]: 
```

### ⛔ GATE: Await User Answers
DO NOT proceed until all GTM questions are answered and validated.
**MANDATORY**: Analyze ALL answers for ambiguities and create follow-up questions if needed.

### Step 3: Write Go-to-Market to Living Document

Append Part 3 to `aiplc-docs/discovery/discovery-document.md`:

```markdown
---

# Part 3: Go-to-Market

## Marketing Strategy
- **Primary Channel**: [Channel]
- **Messaging Framework**:
  - **Tagline**: [Tagline]
  - **Elevator Pitch**: [2-3 sentences]
  - **Key Messages**: [List]
- **Pre-Launch Strategy**: [Description]
- **Launch Assets Needed**: [List]

## Sales Approach
- **Sales Model**: [Self-serve/Inside sales/Field sales/Partner/PLG]
- **Expected Sales Cycle**: [Duration]
- **Key Objections & Responses**:
  | Objection | Response |
  |---|---|
  | [Objection 1] | [Response] |
  | [Objection 2] | [Response] |
- **Sales Enablement Materials**: [List]

## Launch Plan
- **Target Launch Date**: [Date]
- **Launch Strategy**: [Big bang/Soft launch/Beta/Phased]
- **MVP Scope**: [What's in vs. out for launch]
- **Post-Launch Roadmap**: [Key features planned after launch]
- **Launch Milestones**:
  | Milestone | Target Date | Dependencies |
  |---|---|---|
  | [Milestone 1] | [Date] | [Dependencies] |
  | [Milestone 2] | [Date] | [Dependencies] |

## Success Metrics & Monitoring
- **30-Day Success Criteria**: [Criteria]
- **60-Day Success Criteria**: [Criteria]
- **90-Day Success Criteria**: [Criteria]
- **Key Metrics from Day One**: [List]
- **Feedback Collection**: [Mechanism]
- **Kill Criteria**: [Conditions to pivot or stop]
```

Update the document status header:
```markdown
**Status**: Complete — Envision, [Prototype & Validation], Product Strategy, Go-to-Market
```

### Step 4: Present Discovery Phase Completion

```markdown
# 🟣 Discovery Phase Complete

All stages of Discovery are now complete.

## Discovery Document Summary
- **Product**: [Product name]
- **Target Customer**: [Segment]
- **Primary Pain Point**: [Top pain point]
- **Prototype**: [Validated with X users / Skipped]
- **Revenue Model**: [Model]
- **Launch Strategy**: [Strategy]
- **Target Launch Date**: [Date]

## Artifacts
- `aiplc-docs/discovery/discovery-document.md` — Complete living document (all parts)
- `aiplc-docs/discovery/envision/pain-point-analysis.md` — Categorized pain point analysis
- `aiplc-docs/discovery/envision/` — Envision working files
- `aiplc-docs/discovery/prototype/` — Prototype & Validation working files (if executed)
- `aiplc-docs/discovery/product-strategy/` — Product Strategy working files
- `aiplc-docs/discovery/go-to-market/` — Go-to-Market working files

## Next Step
The Discovery Document will be consumed by the **Inception Phase** as input context. Proceeding to **Workspace Detection** → **Requirements Analysis**.

**Please review the complete Discovery Document and confirm to proceed to Inception.**
```

### ⛔ GATE: Await User Approval
DO NOT proceed to Inception Phase until the user explicitly approves the complete Discovery Document.

### Step 5: Update State Tracking

Update `aiplc-docs/aiplc-state.md`:

```markdown
## Stage Progress
### 🟣 DISCOVERY PHASE
- [x] Envision
- [x] Prototype & Validation (or skipped)
- [x] Product Strategy
- [x] Go-to-Market

### 🔵 INCEPTION PHASE
- [ ] Workspace Detection
```

### Step 6: Log and Proceed

- Log completion in `aiplc-docs/audit.md`
- Proceed to Inception Phase (Workspace Detection)
