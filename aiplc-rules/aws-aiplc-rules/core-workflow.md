# DISCOVERY PHASE WORKFLOW (Product Manager Workspace)

## Purpose
This workspace is exclusively for Product Managers to complete the Discovery phase. The output is a comprehensive Discovery Document that will be provided to developers for Inception and Construction phases in a separate workspace.

## Workflow Principle
**The workflow adapts to the work, not the other way around.**

The AI model intelligently assesses which Discovery stages are needed based on:
1. Whether PROTOTYPE-*.md files already exist
2. Whether user wants to start from pain points or use cases
3. Number of use cases to evaluate
4. User's goals (handoff files vs build prototypes)

## MANDATORY: Rule Details Loading
**CRITICAL**: When performing any phase, you MUST read and use relevant content from rule detail files.

Rule details location: `./aws-aiplc-rule-details/`

**Common Rules**: ALWAYS load common rules at workflow start:
- Load `common/process-overview.md` for workflow overview
- Load `common/session-continuity.md` for session resumption guidance
- Load `common/content-validation.md` for content validation requirements
- Load `common/question-format-guide.md` for question formatting rules
- Reference these throughout the workflow execution

## MANDATORY: Content Validation
**CRITICAL**: Before creating ANY file, you MUST validate content according to `common/content-validation.md` rules:
- Validate Mermaid diagram syntax
- Validate ASCII art diagrams (see `common/ascii-diagram-standards.md`)
- Escape special characters properly
- Provide text alternatives for complex visual content
- Test content parsing compatibility

## MANDATORY: Question File Format
**CRITICAL**: When asking questions at any phase, you MUST follow question format guidelines.

**See `common/question-format-guide.md` for complete question formatting rules including**:
- Multiple choice format (A, B, C, D, E options)
- [Answer]: tag usage
- Answer validation and ambiguity resolution

## MANDATORY: Custom Welcome Message
**CRITICAL**: When starting ANY Discovery workflow, you MUST display the welcome message.

**How to Display Welcome Message**:
1. Load the welcome message from `common/welcome-message.md`
2. Display the complete message to the user
3. This should only be done ONCE at the start of a new workflow
4. Do NOT load this file in subsequent interactions to save context space

---

# DISCOVERY PHASE WORKFLOW

## Overview

The Discovery Phase has **THREE ENTRY POINTS**:

1. **Entry Point 1 (Highest Priority)**: Existing PROTOTYPE-*.md files → Build prototypes directly
2. **Entry Point 2 (Path A)**: Start from pain points → PR/FAQ → Solution Analysis
3. **Entry Point 3 (Path B)**: Start from use cases → Prioritization → Prototype Context Generation

---

## Workspace Detection (ALWAYS EXECUTE FIRST)

1. **MANDATORY**: Log initial user request in audit.md with complete raw input
2. Load all steps from `inception/workspace-detection.md`
3. Execute workspace detection:
   - **PRIORITY CHECK**: Check for existing PROTOTYPE-*.md files (Entry Point 1)
     - Path: `aiplc-docs/discovery/prototypes/*/PROTOTYPE-*.md`
     - If found: Skip all discovery, jump to Prototype Building
   - Check for existing aiplc-state.md (resume if found)
   - Check for existing Discovery artifacts
4. Determine next phase:
   - If PROTOTYPE-*.md found: Prototype Building (Entry Point 1)
   - If no PROTOTYPE-*.md: Discovery Mode Selection (Entry Point 2 or 3)
5. **MANDATORY**: Log findings in audit.md
6. Present completion message to user
7. Automatically proceed to next phase

---

## ENTRY POINT 1: Existing PROTOTYPE-*.md Files

**Execute IF**: Workspace Detection finds PROTOTYPE-*.md files

**Purpose**: Build prototypes from pre-generated specifications (typical workshop scenario)

**Flow**:
1. Announce found PROTOTYPE-*.md files
2. **SKIP ALL DISCOVERY PHASES**
3. **JUMP TO**: Prototype Building (see below)
4. After prototypes built, continue to Product Strategy → GTM

---

## ENTRY POINT 2 & 3: Discovery Mode Selection

**Execute IF**: No PROTOTYPE-*.md files found

Load `discovery/discovery-mode-selection.md`

Ask user:
```
How would you like to start Discovery?

[A] Start from customer pain points (create PR/FAQ)
[B] I already have use cases to prioritize

[Answer]:
```

- If [A]: Proceed to **PATH A - Envision**
- If [B]: Proceed to **PATH B - Use Case Intake**

---

## PATH A: Start from Pain Points

### Step 1: Envision

Load `discovery/envision.md`

**Execution**:
1. **MANDATORY**: Log start of Envision in audit.md
2. Determine pain point gathering mode (interactive or URL-based)
3. If URL mode: read ONLY the user-provided URL
4. Gather and confirm customer pain points
5. Generate PR/FAQ document using Working Backwards format
6. **Wait for Explicit Approval**: Present PR/FAQ for review
7. **MANDATORY**: Log user's response in audit.md

### Step 2: Solution Analysis

Load `discovery/solution-analysis.md`

**Execution**:
1. Analyze PR/FAQ to identify solutions
2. Determine: Single solution OR Multiple solutions

**Branch A.1: Single Solution**
- One clear solution from PR/FAQ
- Proceed to Prototype & Validation (single prototype flow)
- Load `discovery/prototype-validation.md`
- Build prototype, iterate, validate
- Continue to Product Strategy → GTM

**Branch A.2: Multiple Solutions**
- PR/FAQ suggests N different solution options
- Extract use cases from PR/FAQ
- **MERGE WITH PATH B** at Use Case Prioritization

---

## PATH B: Start from Use Cases

### Step 1: Use Case Intake

Load `discovery/use-case-intake.md`

**Execution**:
1. **MANDATORY**: Log start in audit.md
2. Ask: "How many use cases?" (could be 3, 5, 10, N)
3. Gather details for all N use cases
4. Categorize: Agentic vs Application
5. Document in `aiplc-docs/discovery/use-case-intake/use-cases.md`

### Step 2: Use Case Prioritization

Load `discovery/use-case-prioritization.md`

**Execution**:
1. Apply prioritization frameworks:
   - Agentic framework for agentic use cases
   - Application framework for application use cases
2. Generate scores for all N use cases
3. Present ranked list
4. User confirms or adjusts
5. Select top 3 for prototyping
6. Document in `aiplc-docs/discovery/prioritization/`

### Step 3: Prototype Context Generation

Load `discovery/prototype-context-generation.md`

**Execution**:
1. For each of top 3 use cases:
   - Gather design context (brand URL)
   - Define requirements (LLM, tools, features)
   - Specify frontend (device, screens)
   - Generate PROTOTYPE-{use-case-slug}.md file
2. Create 3 PROTOTYPE-*.md files in `aiplc-docs/discovery/prototypes/`

### Step 4: Decision Point

Ask user:
```
What would you like to do next?

[A] Build all 3 prototypes now (in this session)
[B] Stop here - hand off PROTOTYPE-*.md files to teams
[C] Build only specific prototypes

[Answer]:
```

**If [A] - Build now**: Proceed to Prototype Building
**If [B] - Hand off**: End Discovery, optionally continue to Product Strategy
**If [C] - Build specific**: Ask which ones, proceed to Prototype Building

---

## Prototype Building (All Paths Converge Here)

Load `discovery/prototype-building.md`

**Execute IF**:
- Entry Point 1: PROTOTYPE-*.md files found
- Path A.1: Single solution from PR/FAQ
- Path A.2 or Path B: User chose to build prototypes

**Execution**:
1. For each PROTOTYPE-*.md file:
   - Read specification
   - Show defaults, ask for LLM provider (ALWAYS ask)
   - Check API credentials
   - Request permission to build
   - Activate Strands Power (if agentic)
   - Build prototype
   - Deploy locally
   - User validates and iterates
2. All prototypes complete

### Selection (if multiple prototypes)

If multiple prototypes built, ask user to select winner for Product Strategy

---

## Product Strategy

Load `discovery/product-strategy.md`

**Execute**: For selected use case

**Execution**:
1. Capture positioning and differentiation
2. Define business model
3. Document strategy decisions
4. **Wait for Explicit Approval**

---

## Go-to-Market

Load `discovery/go-to-market.md`

**Execute**: For selected use case

**Execution**:
1. Marketing strategy
2. Sales approach
3. Launch planning
4. **Wait for Explicit Approval**

---

## Discovery Complete

**Output**: `aiplc-docs/discovery/discovery-document.md`

This comprehensive document contains:
- Pain points and PR/FAQ (if Path A)
- Use cases and prioritization (if Path B)
- Prototype specifications (PROTOTYPE-*.md files)
- Product Strategy
- Go-to-Market plan

**Next Steps for Developers**:
This Discovery Document will be provided to developers in a separate workspace for:
- Inception Phase (Requirements Analysis, Workflow Planning, etc.)
- Construction Phase (Code Generation, Build & Test)
- Operations Phase (Deployment, Monitoring)

---

## Key Principles

- **PM-Focused**: This workspace is for Product Managers only
- **Discovery Only**: No Inception, Construction, or Operations phases
- **Three Entry Points**: Flexible starting points based on situation
- **Workshop-Friendly**: PROTOTYPE-*.md files are portable and shareable
- **Scalable**: Supports any number of use cases (N)
- **Transparent**: Always show defaults, ask for LLM provider
- **Standard AI-PLC**: Uses [Answer]: format throughout
- **Handoff-Ready**: Can stop after generating PROTOTYPE-*.md files
- **Complete Output**: Discovery Document ready for developers

## Audit Logging

**MANDATORY**: Log ALL user inputs and AI responses in `aiplc-docs/audit.md`:
- Capture user's COMPLETE RAW INPUT exactly as provided
- Never summarize or paraphrase user input
- Log every interaction with timestamp
- Use ISO 8601 format (YYYY-MM-DDTHH:MM:SSZ)

**NEVER log the following in audit.md:**
- API keys, tokens, or secrets of any kind
- AWS credentials (access keys, secret keys, bearer tokens)
- Any value that appears to be a credential (strings starting with `AKIA`, `sk-`, `bedrock-api-key-`, `goog_`, etc.)
- If a user accidentally pastes a credential in chat or an answer file, redact it before logging — replace with `[CREDENTIAL REDACTED]`
- Log only "credentials configured: yes/no" — never the actual values

## Directory Structure

```
aiplc-docs/
├── discovery/
│   ├── discovery-document.md          # Main output
│   ├── envision/                      # Path A
│   │   ├── pain-points.md
│   │   └── prfaq.md
│   ├── solution-analysis/             # Path A (if multiple)
│   │   └── identified-solutions.md
│   ├── use-case-intake/               # Path B or Path A.2
│   │   └── use-cases.md
│   ├── prioritization/                # Path B or Path A.2
│   │   ├── framework.md
│   │   ├── scoring.md
│   │   └── ranking.md
│   ├── prototypes/                    # All paths
│   │   ├── {use-case-1-slug}/
│   │   │   ├── PROTOTYPE-{use-case-1-slug}.md  ★ Shareable
│   │   │   ├── design-context.md
│   │   │   └── iteration-log.md
│   │   ├── {use-case-2-slug}/
│   │   │   └── PROTOTYPE-{use-case-2-slug}.md  ★ Shareable
│   │   └── {use-case-3-slug}/
│   │       └── PROTOTYPE-{use-case-3-slug}.md  ★ Shareable
│   ├── product-strategy/
│   │   └── strategy.md
│   └── go-to-market/
│       └── gtm-plan.md
├── aiplc-state.md
└── audit.md
```

## Success Criteria

✅ Discovery Document complete with all sections
✅ PROTOTYPE-*.md files generated (if applicable)
✅ Product Strategy documented
✅ Go-to-Market plan documented
✅ All artifacts ready for developer handoff
✅ Complete audit trail in audit.md

## Handoff to Developers

When Discovery is complete, provide developers with:
1. Complete `aiplc-docs/discovery/` directory
2. Especially `discovery-document.md` (main artifact)
3. All PROTOTYPE-*.md files (if generated)
4. Product Strategy and GTM documents

Developers will use these in their workspace for Inception and Construction phases.
