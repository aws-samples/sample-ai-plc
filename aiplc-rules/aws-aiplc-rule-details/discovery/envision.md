# Envision

**Assume the role** of a product strategist and customer researcher

**Phase**: DISCOVERY PHASE — Stage 1 of 3
**Conditional Phase**: Executes only for Greenfield projects, before Inception.

**Purpose**: Start with a customer problem and structure it into a validated product definition. Gather pain points, synthesize them into a categorized analysis, and generate a PRFAQ using the Working Backwards method.

## Prerequisites
- Workspace Detection must be complete
- Project must be identified as Greenfield

## AI Behavior
The AI acts as a product strategist — asking targeted questions about:
- Target customer segment
- Current workarounds and alternatives
- Pain severity and frequency
- Willingness to change behavior or pay for a solution

## Input Modes

Envision supports three input modes for gathering customer pain points:

### Mode A: Interactive Discovery
The AI asks structured questions to understand the customer's pain points, target audience, and the problem space.

### Mode B: URL/Research Analysis
The user provides a URL (e.g., customer review sites, research reports, competitor analysis). The AI reads **only that URL** and extracts pain points from it. AI does not fetch from any other UrL without permission.

**CRITICAL**: If the user provides a URL, use **only** that URL. Do NOT fetch, reference, or use any other URLs. All pain point understanding must come exclusively from the user-provided URL.

### Mode C: Hybrid (Both)
The user provides a URL for initial context, then the AI asks follow-up questions to fill gaps and deepen understanding. The AI reads **only** the user-provided URL, then supplements with interactive questions.

## Execution Steps

### Step 0: Business Context Gathering

**Purpose**: Establish the business domain and current state before diving into pain points.

#### Step 0.1: Business Context Input Mode Selection

First, ask the user how they want to provide business context. Create `aiplc-docs/discovery/envision/business-context-questions.md` starting with:

```markdown
# Business Context — Input Mode Selection

## Question 1
How would you like to provide your business context information?

A) I will describe it in my own words (free-form text)
B) I have a URL to my business website or relevant page — analyze it for context
C) Both — I have a URL and will also add details in my own words
D) Ask me structured questions — I prefer to answer specific questions
X) Other (please describe after [Answer]: tag below)

[Answer]:
```

### ⛔ GATE: Await Business Context Mode Selection
DO NOT proceed until the user selects their preferred input mode.

#### Step 0.2: Gather Business Context (based on selected mode)

**Mode A — Free-form Text:**
1. Ask the user to describe their business context in their own words
2. Prompt: "Please describe your business — industry, current state, main challenges, target customers, and how you currently solve customer problems. Share as much or as little as you'd like."
3. Analyze the response for completeness against the mandatory areas below
4. If gaps exist, ask targeted follow-up questions only for missing areas

**Mode B — URL Analysis:**
1. Ask the user to provide the URL to their business website or relevant page
2. Fetch and read **only** the provided URL (do NOT fetch any other URLs)
3. Extract business context from the URL content
4. Present extracted context to the user for confirmation
5. If gaps exist against the mandatory areas below, ask targeted follow-up questions only for missing areas

**Mode C — Hybrid (URL + Free-form):**
1. Ask the user to provide the URL first
2. Fetch and read **only** the provided URL
3. Present extracted context to the user
4. Ask the user to add any additional context in their own words
5. Merge both sources and check for completeness against mandatory areas below
6. If gaps exist, ask targeted follow-up questions only for missing areas

**Mode D — Structured Questions:**
1. Present questions covering the mandatory areas below using the standard AIPLC question format (multiple choice with [Answer]: tags, mandatory "Other" option)
2. Analyze answers for completeness
3. Create follow-up questions if needed

#### Mandatory Business Context Areas (for completeness validation)
Regardless of input mode, ensure the following areas are covered before proceeding:
- What industry or business domain is this product for?
- What is the current state of your business in this domain?
- What are the main challenges your business faces today?
- Who are your primary customers or target market?
- What is your business's current approach to solving customer problems?

**MANDATORY**: Analyze responses (from any mode) for completeness against all mandatory areas. Create targeted follow-up questions only for gaps — do not re-ask areas already covered.

### ⛔ GATE: Await Business Context Completion
DO NOT proceed until business context is established.

### Step 1: Determine Input Mode

Create `aiplc-docs/discovery/envision/mode-selection-questions.md`:

```markdown
# Envision — Input Mode Selection

## Question 1
How would you like to provide information about the customer pain points this product should address? Only use the sources I provide and not what you find yourslef or know before hand. Ask for permission if you have additional source information.

A) I will answer questions interactively — ask me about the pain points and target customer
B) I have a URL with relevant research or customer feedback — I will provide it for analysis ; 
C) Both — I have a URL for initial context, and I will also answer follow-up questions
X) Other (please describe after [Answer]: tag below)

[Answer]: 
```

### ⛔ GATE: Await User Answer
DO NOT proceed until the user answers the mode selection question.

### Step 2: Gather Pain Points

#### Step 2A: Interactive Discovery (if Mode A or C selected)

Create `aiplc-docs/discovery/envision/pain-point-questions.md` with questions covering:

**MANDATORY question areas:**
- Who is the target customer? Define the specific customer segment precisely. (e.g., urban professionals under 35 vs. suburban families with kids — specificity matters)
- What problem(s) does the target customer face today? Describe from the customer's perspective.
- How does the customer currently solve or work around this problem? What products, tools, or methods do they use?
- How severe is this pain? (frequency, cost, time wasted, frustration level)
- What would an ideal solution look like from the customer's perspective?
- How many customers have this problem? Is the total addressable market large enough?
- Would customers pay to solve this problem? How much?
- Are there existing products or competitors addressing this problem? How do they fall short?
- What would make the customer switch from their current solution to a new one?

Use the standard AIPLC question format (multiple choice with [Answer]: tags, mandatory "Other" option).

**MANDATORY**: Analyze ALL answers for ambiguities and create follow-up questions if needed. Keep asking until all ambiguities are resolved OR user explicitly asks to proceed.

#### Step 2B: URL/Research Analysis (if Mode B or C selected)

1. Ask the user to provide the URL
2. Fetch and read **only** the provided URL
3. Extract and summarize the pain points found
4. Create `aiplc-docs/discovery/envision/pain-points-from-url.md` documenting:
   - Source URL
   - Extracted pain points (numbered list)
   - Target customer segment (as understood from the URL)
   - Current solutions/workarounds mentioned
   - Gaps or unmet needs identified
   - Severity indicators found
5. Present the extracted pain points to the user for confirmation
6. If Mode C (hybrid): proceed to Step 2A for follow-up questions to fill gaps


### ⛔ GATE: Await Pain Point Confirmation
DO NOT proceed to pain point analysis until the user confirms the pain points are accurate and complete.

### Step 3: Categorized Pain Point Analysis

Synthesize all gathered pain points into `aiplc-docs/discovery/envision/pain-point-analysis.md`:

```markdown
# Categorized Pain Point Analysis

## Target Customer
[Precise customer segment definition]

## Pain Point Categories

### Category 1: [Category Name]
| Pain Point | Severity | Frequency | Current Workaround | Willingness to Pay |
|---|---|---|---|---|
| [Pain point] | [High/Medium/Low] | [Daily/Weekly/Monthly] | [Current solution] | [High/Medium/Low] |

### Category 2: [Category Name]
[Same table format]

## Priority Ranking
1. [Highest priority pain point] — Rationale: [Why this is #1]
2. [Second priority] — Rationale: [Why]
3. [Third priority] — Rationale: [Why]

## Market Assessment
- **Total Addressable Market (TAM)**: [Estimate]
- **Serviceable Addressable Market (SAM)**: [Estimate]
- **Willingness to Pay**: [Summary]
- **Switching Barriers**: [What prevents customers from switching today]

## Competitive Landscape
AI driven 
| Competitor/Alternative | Strengths | Weaknesses | Gap Our Product Fills |
|---|---|---|---|
| [Name] | [Strengths] | [Weaknesses] | [Gap] |

## Key Insights
[Summary of the most important findings that will drive the PRFAQ]
```

### Step 4: Generate PRFAQ with Intelligent Defaults

Using the categorized pain point analysis, generate the PRFAQ. 

**CRITICAL — Intelligent Defaults**: For each PRFAQ section and each clarifying question, provide an intelligent default answer as the first option (Option A), drawn from the pain point analysis context gathered so far. The PM confirms or overrides rather than writing from scratch.

If information is insufficient for any PRFAQ section, create `aiplc-docs/discovery/envision/prfaq-clarifying-questions.md` using the standard AIPLC question format. Each question MUST include an intelligent default as Option A:

```markdown
## Question [Number]
[Question text]

A) [Intelligent default drawn from pain point analysis] ← Suggested based on your pain point analysis
B) [Alternative option]
C) [Alternative option]
X) Other (please describe after [Answer]: tag below)

[Answer]: 
```

### ⛔ GATE: Await PRFAQ Clarifying Question Answers
If clarifying questions were created, DO NOT finalize the PRFAQ until all answers are received and validated.

### Step 5: Write PRFAQ to Living Document

Create `aiplc-docs/discovery/discovery-document.md` and write the Envision section:

**CRITICAL**: Use the PR/FAQ format exactly as defined below. Do NOT deviate from this structure. Template has headers for FYI, actual created file wont have those headers explaining the content, so please dont show them.

```markdown
# Discovery Document

**Product**: [Product Name]
**Date**: [ISO date]
**Status**: In Progress — Envision Complete

---

# Part 1: Envision

## Pain Point Analysis Summary
[Brief summary referencing the full analysis in envision/pain-point-analysis.md]

## PR/FAQ

### Press Release

#### Heading
[Product name so the target customer will understand — one sentence under the title]

#### Subheading
[Describe the customer for the product and what benefits they will gain — one sentence]

#### Summary Paragraph
[City, media outlet, proposed launch date]. [Summary of the product and its benefits.]

#### Problem Paragraph
[Describe the problem(s) the product solves from the customer's point of view. Identify the problem with a large total addressable market. The market size is the number of customers who have this problem multiplied by how much each is willing to pay to solve it.]

#### Solution Paragraph(s)
[Describe the product in detail and how it simply and easily solves the customer's problem. Address how the product is meaningfully differentiated from existing solutions. Include: "Today, customers with this problem use x, y, or z products to meet their needs. Those products fall short of solving x problem(s). Our product addresses these unmet needs in the following ways."]

#### Quotes
**Company Spokesperson Quote:**
> "[Quote from company spokesperson about the product]"

**Customer Quote:**
> "[Quote from a hypothetical customer describing the benefit of using the product]"

#### Getting Started
[Describe how easy it is to get started and where customers can get more information.]

---

### External FAQs (Customer-Facing)

#### Q: What is the price?
A: [Answer]

#### Q: How does it work?
A: [Answer]

#### Q: How do I get help/customer support?
A: [Answer]

#### Q: Where can I buy/access it?
A: [Answer]

[Add additional external FAQs relevant to the specific product]

---

### Internal FAQs (Business & Technical)

#### Q: What products or solutions does the target customer use today to solve this problem?
A: [Answer]

#### Q: What problem(s) does this product solve for customers?
A: [Answer]

#### Q: How does this proposed product solution create value for customers? In what way(s) is this product better, cheaper, and faster than the alternatives?
A: [Answer]

#### Q: What/who are the current competitors for this product?
A: [Answer]

#### Q: How large is the estimated consumer demand, and what is the TAM (total addressable market)?
A: [Answer]

#### Q: How many consumers have this need or problem?
A: [Answer]

#### Q: For how many consumers is this problem big enough that they are willing to spend money to do something about it? If so, how much money would they be willing to spend?
A: [Answer]

#### Q: How many of these consumers have the characteristics/capabilities/constraints necessary to use the product?
A: [Answer]

#### Q: What happens if a customer encounters [edge case]? How does the product deal with [use case]?
A: [Answer]

#### Q: What are the challenging problems (business model, engineering, legal, UI, etc.) that will need to be solved to enable this new product?
A: [Answer]

#### Q: What new capabilities will we need to establish to support this product?
A: [Answer]

#### Q: Do we have any third-party business relationships or dependencies to build this product?
A: [Answer]

#### Q: What third-party technologies are we dependent on for this product to work as promised?
A: [Answer]

#### Q: Are there any potential regulatory or legal issues to consider?
A: [Answer]

#### Q: What are the per-unit economics of the product? What is the expected Gross Profit and Contribution profit per unit?
A: [Answer]

#### Q: How much will we need to invest upfront to build this product (people, technology, inventory, etc.)?
A: [Answer]

#### Q: How will we manage the risk of the upfront investment required?
A: [Answer]

#### Q: Based on the upfront investment and per-unit economics, how many months/years before we achieve profitability?
A: [Answer]

#### Q: What assumptions need to be true for this product to be successful?
A: [Answer]

#### Q: What are the top three reasons this product will not succeed?
A: [Answer]

[Add additional internal FAQs relevant to the specific product]
```

### Step 6: Present Envision Completion

```markdown
# 🔍 Envision Stage Complete

**Input Mode**: [Interactive / URL-Based / Hybrid]
**Pain Points Identified**: [Count]
**Pain Point Categories**: [Count]

## Summary
[Brief summary of the key pain points and proposed product vision from the PRFAQ]

## Artifacts Created
- `aiplc-docs/discovery/discovery-document.md` — Living document (Part 1: Envision)
- `aiplc-docs/discovery/envision/pain-point-analysis.md` — Categorized pain point analysis
- `aiplc-docs/discovery/envision/mode-selection-questions.md` — Mode selection
- [Additional artifacts based on mode used]

## Next Step
Proceeding to **Solution Analysis** to determine if the PRFAQ suggests a single solution or multiple solutions.

**Please review the Envision section of the Discovery Document and confirm to proceed.**
```

### ⛔ GATE: Await User Approval
DO NOT proceed to Solution Analysis until the user explicitly approves the Envision output.

### Step 7: Update State Tracking

Update `aiplc-docs/aiplc-state.md`:

```markdown
## Stage Progress
### 🟣 DISCOVERY PHASE
- [x] Envision
- [ ] Solution Analysis
- [ ] Product Strategy
- [ ] Go-to-Market
```

### Step 8: Log and Proceed

- Log completion in `aiplc-docs/audit.md`
- Proceed to Solution Analysis stage
