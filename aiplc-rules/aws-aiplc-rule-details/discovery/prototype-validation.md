# Prototype & Validation (Path A.1 - Single Solution)

**Assume the role** of a prototype strategist and validation analyst

**Phase**: DISCOVERY PHASE — Path A.1 (Single Solution from PR/FAQ)
**Conditional Phase**: Executes only when:
- Greenfield project
- Path A selected (Pain points)
- Envision complete
- Solution Analysis identifies SINGLE solution
- User wants to validate with prototype

**Note**: This is the ORIGINAL single-prototype flow. For multiple solutions or use case prioritization, see:
- Path A.2: Multiple solutions → `solution-analysis.md` → `use-case-prioritization.md`
- Path B: Use cases → `use-case-intake.md` → `use-case-prioritization.md`
- Entry Point 1: Existing PROTOTYPE-*.md → `prototype-building.md`

**Purpose**: Translate validated scope into a prototype specification, capture design context, guide the AI agent through building a working prototype, structure user validation, synthesize feedback against original pain points, and make a build decision.

## Prerequisites
- Envision stage must be complete and approved
- `aiplc-docs/discovery/discovery-document.md` must exist with Part 1 (Envision) populated
- `aiplc-docs/discovery/envision/pain-point-analysis.md` must exist

## AI Behavior
The AI acts as a prototype strategist — translating Envision artifacts into a buildable spec, guiding design decisions, structuring validation, and synthesizing feedback. The AI does NOT ask the PM to write code or make technical decisions. The PM makes product decisions; the AI handles everything else.

## Execution Steps

### Step 1: Generate Prototype Specification

Load Envision context:
- `aiplc-docs/discovery/discovery-document.md` (Part 1: Envision)
- `aiplc-docs/discovery/envision/pain-point-analysis.md`

The AI derives the prototype scope from the Envision artifacts — not from a blank prompt. Create `aiplc-docs/discovery/prototype/prototype-spec.md`:

```markdown
# Prototype Specification

## Derived from Envision
- **Product**: [From PR/FAQ headline]
- **Target User**: [From pain point analysis — target customer segment]
- **Core Problem**: [Top ranked pain point]

## Proposed Prototype Scope

### Features to Build
| # | Feature | Derived From | Priority | Validates Pain Point |
|---|---|---|---|---|
| 1 | [Feature 1] | PR/FAQ solution paragraph | Must-have | Pain Point #1 |
| 2 | [Feature 2] | Scope definition | Must-have | Pain Point #2 |
| 3 | [Feature 3] | Customer journey friction | Nice-to-have | Pain Point #3 |

### User Flows
1. [User opens app → sees X → does Y → gets Z]
2. [User fills form → submits → sees confirmation]

### Data Model
- [Entity 1]: [key fields]
- [Entity 2]: [key fields]
- [Relationships]

### Out of Scope for Prototype
| Feature | Reason | Deferred To |
|---|---|---|
| [Feature X] | Too complex for validation | Inception |
| [Feature Y] | Not needed to test core hypothesis | Post-launch |

## Validation Hypothesis
- **Primary hypothesis**: [What this prototype will prove or disprove]
- **Success criteria**: [Measurable criteria for "validated"]
- **Target users for validation**: [Count and segment]
- **Validation duration**: [Recommended timeframe]
```

**CRITICAL — Intelligent Defaults**: Every feature and scope decision includes rationale traced back to Envision artifacts. The PM confirms or adjusts — not writes from scratch.

Present the spec to the user with:

```markdown
Based on your Envision work, here is the proposed prototype scope.

[Display spec summary — features, user flows, validation hypothesis]

Does this capture what you want to validate?

A) Yes, proceed to design context  ← Suggested
B) I want to add or remove features (describe below)
C) I want to start with something simpler — just the core workflow
X) Other (please describe after [Answer]: tag below)

[Answer]:
```

If the user selects B or X, revise the spec based on their input and re-present.

### ⛔ GATE: Await User Approval of Prototype Spec
DO NOT proceed until the user confirms the prototype scope.

### Step 2: Design Context

Create `aiplc-docs/discovery/prototype/design-context.md` with questions:

```markdown
# Prototype Design Context

## Question 1
What should this prototype look like?

A) Clean and modern — use a professional default design (good for most validation scenarios)
B) Match my organization's brand — I will provide brand guidelines, colors, logo, or a reference
C) Match a specific product or tool our users already use — I will provide a reference
D) Minimal — focus on functionality, not appearance (internal validation only)
X) Other (please describe after [Answer]: tag below)

[Answer]:
```

#### If Option B selected (Organization Brand):

```markdown
## Question 2: Brand Details
Provide any of the following that you have. Leave blank what you don't have.

- Brand colors (primary, secondary, accent): [Answer]
- Logo file path or URL: [Answer]
- Font preference: [Answer]
- Reference URL (your company website, existing product, or internal tool): [Answer]
- Design system name (e.g., "we use Material Design", "we follow Cloudscape", "we use Ant Design"): [Answer]

[Answer]:
```

#### If Option C selected (Match Existing Product):

```markdown
## Question 2: Reference Product
What product or tool should this feel similar to?

A) I will provide a URL — the AI will analyze the visual style
B) Name a well-known product (e.g., "Salesforce-like", "Notion-like", "Jira-like", "AWS Console-like", "Slack-like")
X) Other (please describe after [Answer]: tag below)

[Answer]:
```

#### Device context (always ask):

```markdown
## Question 3
What is the primary device for your users?

A) Desktop browser  ← Suggested for enterprise/internal tools
B) Mobile phone
C) Tablet
D) Both desktop and mobile (responsive)
X) Other (please describe after [Answer]: tag below)

[Answer]:
```

**MANDATORY**: Analyze answers and resolve any ambiguities before proceeding.

### ⛔ GATE: Await Design Context Answers
DO NOT proceed until all design context questions are answered.

### Step 3: Build Prototype

Generate `aiplc-docs/discovery/prototype/build-instructions.md`:

This file combines the prototype spec (Step 1) and design context (Step 2) into build instructions for the AI agent.

```markdown
# Prototype Build Instructions

**Context**: This is a rapid prototype for validation — NOT production code.

**Optimize for**: Speed, working UI, core workflow completeness
**Deprioritize**: Security hardening, error handling edge cases, scalability, code quality, extensive test coverage

## Features to Implement
[From prototype-spec.md — numbered list with acceptance criteria]

## User Flows
[From prototype-spec.md]

## Data Model
[From prototype-spec.md]

## Design Requirements

### [Based on design-context.md answers]

#### If Clean and Modern (Option A):
- Use a modern CSS framework (Tailwind CSS, Shadcn/UI, or equivalent)
- Neutral color palette: slate/gray tones with one accent color
- Clean typography with adequate whitespace
- Responsive layout if desktop+mobile selected
- Professional but not branded — suitable for any audience

#### If Organization Brand (Option B):
- Primary color: [from PM input]
- Secondary color: [from PM input]
- Accent color: [from PM input or derived]
- Logo: [file path or URL — place in header/nav]
- Font: [from PM input or default to system font stack]
- Design system: [if specified, use its component library]
- Reference URL: [if provided, match general visual density, layout patterns, and chrome style]
- Apply brand colors to: navigation, buttons, links, active states, headers
- Match the overall visual feel of the reference — NOT pixel-perfect copy

#### If Match Existing Product (Option C):
- Reference product: [name or URL]
- Visual patterns to match:
  - Navigation style (sidebar, top nav, breadcrumbs)
  - Layout approach (cards, tables, dense/spacious)
  - Interaction patterns (modals, inline editing, drag-drop)
  - Visual density and chrome level
- Do NOT copy logos, trademarks, or exact layouts — match the feel, not the pixels

#### If Minimal (Option D):
- Basic HTML with system fonts
- Functional layout only — no styling effort
- Standard form elements, tables, buttons
- No color scheme, no branding, no visual polish

### Device
- Primary: [Desktop / Mobile / Tablet / Responsive]
- [If responsive: mobile-first or desktop-first based on primary]

## Technical Guidance
- Use the simplest technology stack that works
- Prefer local-first storage (SQLite, file-based, in-memory) unless cloud deployment is configured
- If cloud deployment is available (AWS credentials, Amplify, CDK), deploy and provide URL
- If cloud deployment is not available, provide local run instructions
- Frontend: lightweight framework or plain HTML/CSS/JS
- Backend: single service, minimal dependencies
- Tests: happy path only — enough to verify core flows work
```

**Instruct the AI agent to build the prototype from this file.**

The AI agent reads `build-instructions.md` and generates the application code in the workspace, following the same code generation patterns used in the Construction phase but with relaxed quality constraints:

- Skip detailed functional design
- Skip NFR requirements and design
- Skip infrastructure design
- Minimal test coverage (happy path only)
- No security hardening
- No performance optimization

**If deployment is available** (AWS credentials configured, Amplify/CDK available): deploy and provide URL.

**If deployment is not available**: provide local run instructions and suggest a tunneling option for sharing with external users (e.g., ngrok, localtunnel, or similar).

Present completion:

```markdown
# Prototype Built

[If deployed]: Your prototype is live at: [URL]
[If local]: Run with: `[command]`. To share externally: `[tunnel command]`

**Design**: [Clean modern / Organization brand / Matching [product] / Minimal]
**Device**: [Desktop / Mobile / Responsive]

**Features implemented**:
- [Feature 1] ✓
- [Feature 2] ✓
- [Feature 3] ✓ (partial — [limitation noted])

**Known limitations**:
- [Limitation 1]
- [Limitation 2]

What would you like to do?

A) Review and iterate — I want to make changes
B) Proceed to validation — share with target users
C) Rebuild with different design — I want to change the look and feel

[Answer]:
```

### ⛔ GATE: Await User Response

### Step 4: Iterate

The PM describes changes in natural language. Changes can be functional OR visual:

**Functional changes**:
- "Add a priority field to the form"
- "Add email notifications when a risk score changes"
- "Remove the settings page — not needed for validation"

**Visual/Design changes**:
- "Make it look more like our company's internal tools — darker theme, denser layout"
- "Add our logo and change the blue to our brand green (#2E8B57)"
- "The fonts are too large — make everything more compact"
- "Can you make the dashboard look more like Datadog?"

For each change request, the AI agent:

1. Analyzes the request
2. Describes what will change (functional and/or visual)
3. Waits for PM approval
4. Applies the change
5. Logs the iteration in `aiplc-docs/discovery/prototype/iteration-log.md`

```markdown
## Iteration [Number]
**Request**: "[PM's exact words]"
**Changes applied**:
- [Change 1]
- [Change 2]
**Type**: [Functional / Visual / Both]
```

**Repeat iteration until the PM is satisfied.**

After the PM confirms satisfaction:

```markdown
Your prototype is ready for validation.

A) Proceed to validation setup
B) I want to make more changes

[Answer]:
```

### ⛔ GATE: Await User Confirmation to Proceed to Validation

### Step 5: Validation Setup

Create `aiplc-docs/discovery/prototype/validation-plan.md`:

```markdown
# Validation Plan

## Question 1
How will you collect feedback from target users?

A) I will conduct interviews or demos and report findings here
B) I will send a survey and import results
C) I will share the prototype link and collect informal feedback
D) I have analytics or usage data I can import
E) A combination of the above
X) Other (please describe after [Answer]: tag below)

[Answer]:

## Question 2
How many target users will you validate with?

A) 3-5 users  ← Suggested for early-stage validation
B) 6-10 users
C) 11-20 users
D) 20+ users
X) Other (please describe after [Answer]: tag below)

[Answer]:

## Question 3
What is your validation timeline?

A) 1 week  ← Suggested
B) 2 weeks
C) 3-4 weeks
D) I already have feedback ready to import now
X) Other (please describe after [Answer]: tag below)

[Answer]:
```

If the user selects Option D (feedback ready now), proceed immediately to Step 6.

Otherwise, present:

```markdown
Validation plan set.

- **Method**: [From Q1]
- **Users**: [From Q2]
- **Timeline**: [From Q3]

When you have collected feedback, return and provide it. You can:
- Paste feedback text directly
- Provide a file path to import (.md, .docx, .csv)
- Describe findings verbally

I will synthesize everything against your original pain points.
```

### ⛔ GATE: Await Validation Completion
Wait for the user to return with feedback data. DO NOT proceed until the user provides feedback or explicitly asks to skip validation.

### Step 6: Feedback Import and Synthesis

When the user returns with feedback, synthesize it and create `aiplc-docs/discovery/prototype/validation-results.md`:

```markdown
# Validation Results

## Feedback Sources
| Source | Type | Users | Feedback Items |
|---|---|---|---|
| [Source 1] | [Interview / Survey / Usage data / Informal] | [Count] | [Count] |

## Theme Analysis
| Theme | Frequency | Severity | Representative Quote |
|---|---|---|---|
| [Theme 1] | [X of Y users] | [High / Medium / Low] | "[Quote]" |
| [Theme 2] | [X of Y users] | [High / Medium / Low] | "[Quote]" |

## Feature Validation
| Feature | Signal | User Feedback Summary |
|---|---|---|
| [Feature 1] | Validated ✓ | [Summary] |
| [Feature 2] | Partially validated | [Summary — what worked, what didn't] |
| [Feature 3] | Not tested | [Users did not reach this feature] |

## Pain Point Mapping
| Original Pain Point | Validated? | Evidence |
|---|---|---|
| Pain Point #1: [Name] | [Yes / Partial / No / Not tested] | [Evidence] |
| Pain Point #2: [Name] | [Yes / Partial / No / Not tested] | [Evidence] |
| Pain Point #3: [Name] | [Yes / Partial / No / Not tested] | [Evidence] |

## Unmet Needs Discovered
| Need | Frequency | Recommended Action |
|---|---|---|
| [Need 1] | [X users mentioned] | [Add to Inception / Defer to post-launch / Ignore] |

## Design Feedback
| Feedback | Frequency | Action Taken |
|---|---|---|
| [Design feedback 1] | [X users] | [Applied in iteration / Deferred / Not actionable] |

## Key Insights
[AI-synthesized summary of the most important validation findings — what was validated, what was not, what surprised us, and what it means for the product direction]
```

Present to user for confirmation:

```markdown
# Validation Results Summary

**Users**: [Count] | **Duration**: [Days] | **Feedback items**: [Count]

**Pain points validated**: [X of Y]
**Top themes**:
1. [Theme 1] ([X users])
2. [Theme 2] ([X users])
3. [Theme 3] ([X users])

**Unmet needs discovered**: [Count]

Please review the full validation results and confirm accuracy.

A) Results are accurate — proceed to build decision
B) I have corrections or additional context to add
X) Other (please describe after [Answer]: tag below)

[Answer]:
```

### ⛔ GATE: Await Confirmation of Validation Results

### Step 7: Build Decision

Based on validation results, generate a recommendation:

```markdown
# Build Decision

Based on validation results, here is my assessment:

**Recommendation**: [PROCEED / ITERATE / PIVOT / KILL]

**Rationale**:
- Pain points validated: [X of Y]
- [Key supporting signal]
- [Key risk or concern]
- [Unmet needs to address]

## Question 1
What is your decision?

A) Proceed to Product Strategy — take this validated prototype forward
   ← [Suggested if majority of pain points validated]
B) Iterate — make changes to the prototype and re-validate
C) Pivot — rethink the approach based on feedback (return to Envision with new context)
D) Kill — insufficient signal to continue (archive artifacts, end workflow)
X) Other (please describe after [Answer]: tag below)

[Answer]:
```

### ⛔ GATE: Await Build Decision

**If Iterate (B)**: Return to Step 4. Apply changes, re-validate.
**If Pivot (C)**: Return to Envision stage with validation feedback as new input context.
**If Kill (D)**: Log decision in audit.md, archive artifacts, end workflow.
**If Proceed (A)**: Continue to Step 8.

### Step 8: Write to Living Document

Append Part 2 to `aiplc-docs/discovery/discovery-document.md`:

```markdown
---

# Part 2: Prototype & Validation

## Prototype Spec
[Summary referencing full spec in prototype/prototype-spec.md]
- **Features built**: [List]
- **Design approach**: [Clean modern / Organization brand / Matching [product] / Minimal]
- **Device target**: [Desktop / Mobile / Responsive]

## Build Approach
- **Technology**: [Stack used by the AI agent]
- **Deployment**: [URL if deployed / Local if not]
- **Iterations**: [Count] — [Summary of key changes]

## Validation Results
[Summary referencing full results in prototype/validation-results.md]
- **Users**: [Count] | **Duration**: [Days] | **Feedback items**: [Count]
- **Pain points validated**: [X of Y]
- **Top user requests**: [List]
- **Unmet needs discovered**: [List]

## Build Decision: [PROCEED / ITERATE / PIVOT / KILL]
- **Rationale**: [AI-synthesized rationale + PM decision]
- **Recommendations for Inception**: [Features to add, modify, or remove based on validation]
```

Update the document status header:
```markdown
**Status**: In Progress — Envision Complete, Prototype & Validation Complete
```

### Step 9: Present Completion

```markdown
# Prototype & Validation Stage Complete

**Prototype**: [Deployed URL or local path]
**Design**: [Approach used]
**Validation**: [X] users, [Y] days, [Z] feedback items
**Build Decision**: [PROCEED / ITERATE / PIVOT / KILL]

## Artifacts Created
- `aiplc-docs/discovery/discovery-document.md` — Living document (Part 2: Prototype & Validation added)
- `aiplc-docs/discovery/prototype/prototype-spec.md` — Prototype specification
- `aiplc-docs/discovery/prototype/design-context.md` — Design context and brand guidelines
- `aiplc-docs/discovery/prototype/build-instructions.md` — Build instructions for AI agent
- `aiplc-docs/discovery/prototype/iteration-log.md` — Iteration history
- `aiplc-docs/discovery/prototype/validation-plan.md` — Validation plan
- `aiplc-docs/discovery/prototype/validation-results.md` — Validation results and synthesis

## Next Step
Proceeding to **Product Strategy** to capture positioning, differentiation, and business model decisions — informed by validated prototype and real user feedback.

**Please review the Prototype & Validation section of the Discovery Document and confirm to proceed.**
```

### ⛔ GATE: Await User Approval
DO NOT proceed to Product Strategy until the user explicitly approves.

### Step 10: Update State Tracking

Update `aiplc-docs/aiplc-state.md`:

```markdown
## Stage Progress
### 🟣 DISCOVERY PHASE
- [x] Envision
- [x] Prototype & Validation
- [ ] Product Strategy
- [ ] Go-to-Market
```

### Step 11: Log and Proceed

- Log completion in `aiplc-docs/audit.md`
- Proceed to Product Strategy stage
