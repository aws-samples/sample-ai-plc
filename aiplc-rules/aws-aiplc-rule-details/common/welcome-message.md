# AI-PLC Welcome Message

**Purpose**: This file contains the user-facing welcome message that should be displayed ONCE at the start of any AI-PLC workflow.

---

# 👋 Welcome to AI-PLC Discovery Phase! 👋

I'll guide you through the Discovery phase - a Product Manager-focused workflow for defining and validating product ideas before development begins.

## What is AI-PLC Discovery?

AI-PLC Discovery is a structured yet flexible product definition process that helps Product Managers:

- **Gather and analyze customer pain points** from various sources
- **Create compelling PR/FAQs** using the Working Backwards method
- **Prioritize use cases** when evaluating multiple options
- **Generate prototype specifications** that teams can build from
- **Build and validate prototypes** (optional) to test ideas quickly
- **Define product strategy** and go-to-market plans
- **Document everything** for seamless handoff to developers

## The Discovery Phase - Three Entry Points

```
                    Product Manager Request
                              |
                              v
                    Workspace Detection
                              |
                              v
                  Check for PROTOTYPE-*.md files?
                              |
            ┌─────────────────┼─────────────────┐
            |                 |                 |
            v                 v                 v
    Entry Point 1      Entry Point 2      Entry Point 3
    Existing Files     Pain Points        Use Cases
            |                 |                 |
            |                 v                 v
            |           Envision          Use Case Intake
            |           (PR/FAQ)                |
            |                 |                 v
            |                 v           Prioritization
            |          Solution Analysis       |
            |                 |                 v
            |        ┌────────┴────────┐  Context Generation
            |        |                 |       |
            |        v                 v       |
            |   Single Solution   Multiple     |
            |        |            Solutions    |
            |        v                 |       |
            |   Prototype &            └───────┘
            |   Validation                 |
            |        |                     v
            └────────┴─────────────────────┘
                              |
                              v
                    Prototype Building
                         (Optional)
                              |
                              v
                      Product Strategy
                              |
                              v
                       Go-to-Market
                              |
                              v
        ╔═══════════════════════════════════════╗
        ║   DISCOVERY DOCUMENT COMPLETE         ║
        ║   Ready for Developer Handoff         ║
        ╚═══════════════════════════════════════╝
```

### Discovery Phase Overview:

**DISCOVERY PHASE** - *PM-Led Product Definition*
- **Purpose**: Defines WHO the customer is, WHAT problem to solve, and WHY it matters — before any technical work begins
- **Three Entry Points**:
  1. **Existing PROTOTYPE-*.md files**: Build prototypes directly (workshop scenario)
  2. **Pain Points (Path A)**: Gather pain points → PR/FAQ → Solution Analysis
  3. **Use Cases (Path B)**: Gather use cases → Prioritize → Generate prototype specs

### Three Entry Points - Detailed Explanation:

#### 📄 Entry Point 1: Existing PROTOTYPE-*.md Files
**When to use**: You already have prototype specification files

**What happens**:
- Workspace Detection finds PROTOTYPE-*.md files
- Skips all discovery phases
- Jumps directly to Prototype Building
- Builds prototypes from specifications

**Typical scenario**: Workshop where facilitator distributed PROTOTYPE-*.md files to teams

**Example**: You receive `PROTOTYPE-customer-support-agent.md` → workflow builds it immediately

---

#### 💡 Entry Point 2: Pain Points (Path A)
**When to use**: Starting from customer pain points or feedback

**What happens**:
1. Choose [A] Start from customer pain points
2. Gather pain points (from URLs or interactively)
3. Generate PR/FAQ using Working Backwards
4. Solution Analysis identifies single or multiple solutions
5. Build prototype(s)
6. Product Strategy → Go-to-Market

**Typical scenario**: You have customer reviews/feedback and want to create a solution

**Example**: Provide Trustpilot URL → workflow creates PR/FAQ → builds prototype

---

#### 📊 Entry Point 3: Use Cases (Path B)
**When to use**: You have identified use cases needing prioritization

**What happens**:
1. Choose [B] I already have use cases
2. Provide details for N use cases (3, 5, 10, 20+)
3. Prioritize using frameworks (agentic vs application)
4. Select top 3 for prototyping
5. Generate PROTOTYPE-*.md files
6. Optionally build prototypes
7. Product Strategy → Go-to-Market

**Typical scenario**: Product team has 10 potential use cases, needs to prioritize

**Example**: 10 agent ideas → prioritize → get PROTOTYPE-*.md for top 3 → build

---

- **Activities**: 
  - Gathering customer pain points (interactive or URL-based)
  - Creating PR/FAQ using Working Backwards
  - Prioritizing use cases (supports N use cases, selects top 3)
  - Generating PROTOTYPE-*.md files (portable, shareable specifications)
  - Building and validating prototypes (optional)
  - Defining product strategy
  - Planning go-to-market
- **Output**: 
  - **Main Artifact**: `discovery-document.md` - comprehensive Discovery Document
  - **Prototype Specs**: PROTOTYPE-*.md files for each use case
  - **Strategy Docs**: Product Strategy and GTM plans
- **Your Role**: Lead the product vision, answer questions, review and approve each stage

**What Happens After Discovery?**
- Developers receive the Discovery Document in a **separate workspace**
- They use it for **Inception Phase** (Requirements Analysis, Workflow Planning)
- Then **Construction Phase** (Code Generation, Build & Test)
- Finally **Operations Phase** (Deployment, Monitoring)

## Key Principles:

- 🎯 **PM-Focused**: This workspace is exclusively for Product Managers
- 🚀 **Three Entry Points**: Flexible starting points based on your situation
- 📊 **Scalable**: Supports any number of use cases (3, 5, 10, 20+)
- 🔄 **Workshop-Friendly**: PROTOTYPE-*.md files are portable and shareable
- 🔍 **Transparent**: Always shows defaults, asks for your input
- 📝 **Documented**: Complete audit trail of all decisions
- 🤝 **Handoff-Ready**: Produces comprehensive Discovery Document for developers
- ⚡ **Adaptive**: Workflow adjusts based on your needs

## What Happens Next:

1. **I'll check your workspace** for existing PROTOTYPE-*.md files
   - If found: We'll build prototypes directly (Entry Point 1)
   - If not found: I'll ask how you want to start

2. **You'll choose your path** (if no existing files):
   - **Path A**: Start from customer pain points → Create PR/FAQ
   - **Path B**: Start from use cases → Prioritize and select top 3

3. **We'll work through Discovery stages**:
   - Gather pain points or use cases
   - Prioritize (if multiple options)
   - Generate PROTOTYPE-*.md files
   - Optionally build prototypes
   - Define Product Strategy
   - Plan Go-to-Market

4. **You'll get a complete Discovery Document** ready to hand off to developers

The Discovery workflow adapts to:
- 📋 Whether you have existing prototype specs
- 🎯 Whether you're starting from pain points or use cases
- 📊 How many use cases you need to evaluate
- 🔨 Whether you want to build prototypes or just generate specs

Let's begin your Discovery journey!
