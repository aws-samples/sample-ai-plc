# Vision Document Generation

**Assume the role** of a product owner preparing a build-ready handoff

**Phase**: DISCOVERY PHASE — Final Output (runs after Go-to-Market on every path)
**Also invocable**: As a standalone entry point against an existing `discovery-document.md` (see core-workflow.md, Entry Point 4).

**Purpose**: Transform the completed Discovery Document into an **AI-DLC Vision Document** — the exact input format the AI-DLC workflow (`awslabs/aidlc-workflows`) consumes as the primary input to its Inception Phase. This makes the AI-PLC → AI-DLC handoff native: the PM finishes Discovery and receives a `vision-document.md` that a developer can drop directly into an AI-DLC workspace to start a build.

**Why this exists**: AI-DLC's Requirements Analysis and Workflow Planning stages are driven by a structured Vision Document (Executive Summary, Business Context, Full Scope Vision, MVP Scope with explicit IN/OUT tables, Risks, and Open Questions). The AI-PLC Discovery Document contains almost all of this content, but organized around Working Backwards (PR/FAQ, Product Strategy, Go-to-Market) rather than AI-DLC's schema. This module reshapes — it does not re-interview.

## Prerequisites
- `aiplc-docs/discovery/discovery-document.md` must exist and be complete
  - Standard flow: all stages through Go-to-Market approved
  - Standalone flow (Entry Point 4): any existing Discovery Document, even a partial one — note gaps where sections are missing
- Reference the AI-DLC Vision Document spec if available in the workspace: `docs/writing-inputs/vision-document-guide.md`. If not present, use the mapping and template in this file — they conform to that spec.

## Execution Steps

### Step 1: Load All Discovery Context

Load every available artifact — do not rely on the summary sections alone:
- `aiplc-docs/discovery/discovery-document.md` (all parts: Envision, Prototype & Validation if executed, Product Strategy, Go-to-Market)
- `aiplc-docs/discovery/envision/pain-point-analysis.md` (categorized pain points, severity, market sizing)
- `aiplc-docs/discovery/envision/prfaq.md` (press release + FAQs)
- `aiplc-docs/discovery/prioritization/` (scoring and ranking, if Path B or Path A.2)
- `aiplc-docs/discovery/prototypes/*/PROTOTYPE-*.md` (prototype specifications, if generated)
- `aiplc-docs/discovery/product-strategy/strategy.md`
- `aiplc-docs/discovery/go-to-market/gtm-plan.md`

Every field in the Vision Document MUST be grounded in these artifacts. Do not invent product scope, users, or metrics that discovery did not establish.

### Step 2: Map Discovery Content → Vision Document Sections

Use this mapping. Most sections are a direct reshape of existing content:

| Vision Document Section | Sourced From | Notes |
|---|---|---|
| Executive Summary | PR/FAQ press release headline + summary paragraph | Rewrite in Vision's "[Product] is a [type] that enables [users] to [capability]" form. No marketing language. |
| Problem Statement | Pain Point Analysis (top pain points) | Be concrete; cite the specific validated pain point. |
| Business Drivers | PR/FAQ "why now", Product Strategy timing | Market/competitive/regulatory pressure that makes this timely. |
| Target Users & Stakeholders | Pain points personas + PR/FAQ customer quotes | One table row per user type: Role / Who they are / Primary need. |
| Business Constraints | Product Strategy (cost drivers, pricing), GTM | Non-negotiable boundaries only. |
| Success Metrics | GTM 30/60/90-day criteria + day-one metrics; Product Strategy KPIs | Table: Metric / Current State / Target / Measurement Method. Use "TBD" for baseline if discovery did not establish one — do not fabricate. |
| Full Scope Vision — Product Vision Statement | Product Strategy positioning + value proposition | Aspirational end-state. |
| Full Scope Vision — Feature Areas | Solution Analysis + PROTOTYPE-*.md capabilities + GTM post-launch roadmap | Group into logical feature areas with capabilities + user value. |
| Integration Points | PROTOTYPE-*.md (LLM, tools, external systems) | External systems/APIs the full system integrates with. |
| User Journeys (Full Vision) | PR/FAQ customer scenario + prototype flows | 2-3 end-to-end journeys. |
| Scalability & Growth | Product Strategy expansion path | Adjacent segments, geographies, volumes. |
| Long-Term Roadmap | GTM post-launch roadmap + prioritization ranking | MVP / Phase 2 / Phase 3 table. |
| MVP Scope — Objective | GTM MVP scope + top-priority use case | 1-2 sentences: the single most important thing the MVP proves. |
| MVP Scope — Success Criteria | GTM launch success criteria | Testable checkboxes. |
| MVP Features IN | GTM "MVP scope: what's in", prioritization top pick, PROTOTYPE-*.md | Explicit table. If not listed, it is not in the MVP. |
| MVP Features OUT | GTM "what's out for launch", deprioritized use cases | Table with reason for deferral + target phase. Prevents scope creep. |
| MVP User Journeys | Prototype flows (simplified) | Note limitation vs. full vision per journey. |
| MVP Constraints & Assumptions | Product Strategy assumptions, prototype scope | Assumption + risk-if-wrong. |
| Risks & Dependencies | **AUTO-INFERRED** (see Step 3) | — |
| Open Questions | **AUTO-INFERRED** (see Step 3) | — |

### Step 3: Auto-Infer Risks and Open Questions (No PM Questions)

AI-PLC does not collect a Risks table or Open Questions list during Discovery. **Do NOT ask the PM new questions for these** — infer them from the discovery context already loaded, then flag them clearly for PM review.

**Risks** — derive from:
- Assumptions in Product Strategy that, if wrong, break the model
- Pain points with weak/unvalidated evidence (especially if Prototype & Validation was skipped)
- Competitive/defensibility gaps noted in differentiation
- GTM kill criteria (each kill condition implies a risk)

Produce a table: Risk / Likelihood (High/Med/Low) / Impact (High/Med/Low) / Mitigation.

**Open Questions** — derive from:
- Anything marked "TBD", assumed, or unvalidated in the discovery artifacts
- Success metrics without an established baseline
- Integration points named but not specified
- Any place strategy said "based on Envision findings only" (i.e., prototype validation skipped)

Produce a checkbox list. These feed AI-DLC's Requirements Analysis as pre-declared clarifying questions, so make them specific and answerable.

**MANDATORY**: Prefix both sections in the output with:
`> _Note: Risks and Open Questions below are AI-inferred from your Discovery work, not directly captured during Discovery. Please review and adjust before handoff._`

### Step 4: Write the Vision Document

Write `aiplc-docs/discovery/vision-document.md` using the template below. This template conforms to AI-DLC's `vision-document-guide.md`.

```markdown
# Vision Document: [Product Name]

**Source**: Generated by AI-PLC Discovery from `aiplc-docs/discovery/discovery-document.md`
**Target Workflow**: AI-DLC (awslabs/aidlc-workflows) — Inception Phase input
**Status**: Ready for AI-DLC Inception (Vision input). Technical Environment Document to be authored in the build workspace.

---

## Executive Summary

[Product Name] is a [type of system/product] that enables [target users] to [core capability]. It addresses [business problem] by [approach/differentiation]. The expected outcome is [measurable business result].

---

## Business Context

### Problem Statement
[Concrete problem from Pain Point Analysis.]

### Business Drivers
[Why now — from PR/FAQ and Product Strategy.]

### Target Users and Stakeholders
| User Type | Description | Primary Need |
|-----------|-------------|--------------|
| [Role] | [Who they are] | [What they need] |

### Business Constraints
[Non-negotiable boundaries.]

### Success Metrics
| Metric | Current State | Target State | Measurement Method |
|--------|--------------|--------------|-------------------|
| [Metric] | [Baseline or TBD] | [Goal] | [How measured] |

---

## Full Scope Vision

### Product Vision Statement
[Aspirational end-state from Product Strategy.]

### Feature Areas
#### Feature Area 1: [Name]
- **Description**: [What it covers]
- **Key Capabilities**:
  - [Capability]
- **User Value**: [Why it matters]

### Integration Points
- [System/Service] - [Purpose]

### User Journeys (Full Vision)
#### Journey 1: [Name]
1. [Step]
**Outcome**: [What the user achieves]

### Scalability and Growth
[Expansion path from Product Strategy.]

### Long-Term Roadmap
| Phase | Focus | Timeframe |
|-------|-------|-----------|
| MVP | [Core scope] | [Target] |
| Phase 2 | [Expansion] | [Target] |

---

## MVP Scope

### MVP Objective
[1-2 sentences.]

### MVP Success Criteria
- [ ] [Criterion]

### Features In Scope (MVP)
| Feature | Description | Priority | Rationale for Inclusion |
|---------|-------------|----------|------------------------|
| [Feature] | [Description] | Must Have | [Why it cannot be deferred] |

### Features Explicitly Out of Scope (MVP)
| Feature | Reason for Deferral | Target Phase |
|---------|-------------------|--------------|
| [Feature] | [Why it can wait] | [Phase 2/3/TBD] |

### MVP User Journeys
#### Journey 1: [Name]
1. [Step]
**Outcome**: [What the user achieves]
**Limitation vs Full Vision**: [What is simplified]

### MVP Constraints and Assumptions
- **Assumption**: [Statement] - **Risk if wrong**: [Consequence]

### MVP Definition of Done
- [ ] All "Must Have" features implemented and tested
- [ ] [Project-specific criterion]

---

## Risks and Dependencies

> _Note: Risks and Open Questions below are AI-inferred from your Discovery work, not directly captured during Discovery. Please review and adjust before handoff._

### Key Risks
| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| [Risk] | [High/Med/Low] | [High/Med/Low] | [Mitigation] |

### External Dependencies
- [Dependency] - [Owner] - [Status]

### Open Questions
- [ ] [Specific, answerable question feeding AI-DLC Requirements Analysis]
```

**Content validation**: Before writing, validate per `common/content-validation.md` (Mermaid/ASCII syntax, special-character escaping). Do NOT list technologies, languages, or implementation details in the Vision Document — that belongs in AI-DLC's Technical Environment Document, authored in the build workspace.

### Step 5: Present Completion

```markdown
# 🎯 Vision Document Generated

Your Discovery work has been transformed into an **AI-DLC Vision Document** — ready to hand off to a build team.

## Summary
- **Product**: [Product name]
- **MVP Objective**: [One line]
- **Features IN (MVP)**: [count]
- **Features OUT (deferred)**: [count]
- **Risks flagged for review**: [count]
- **Open Questions for Inception**: [count]

## Artifact
- `aiplc-docs/discovery/vision-document.md` — AI-DLC Inception input (Vision)

## ⚠️ Review Needed
The **Risks** and **Open Questions** sections were AI-inferred from your Discovery work. Please review and adjust before handoff.

## Next Step (Handoff to AI-DLC)
1. Set up an AI-DLC workspace (`awslabs/aidlc-workflows`) in a **separate folder**.
2. Copy `vision-document.md` into that workspace.
3. Author a **Technical Environment Document** there (languages, frameworks, cloud services, security) — this is the build team's decision, not the PM's.
4. Start AI-DLC and point Requirements Analysis at the Vision Document.
```

### ⛔ GATE: Await User Review
Present the Vision Document and STOP. Do not consider Discovery output complete until the PM has reviewed the AI-inferred Risks and Open Questions.

### Step 6: Update State Tracking

Update `aiplc-docs/aiplc-state.md`.

**CRITICAL — Overwrite, do NOT append**: Locate the existing `## Stage Progress` block and the `## Handoff Artifacts` block (if present) and **replace them in place** with the versions below. Do NOT append a second copy. After editing, verify there is exactly ONE `## Stage Progress` block and exactly ONE `## Handoff Artifacts` block, with NO leftover or duplicate checklist lines (e.g., a stray unchecked `- [ ] Vision Document Generation` or `- [ ] Product Strategy` from an earlier template). Every item under Handoff Artifacts must be checked `[x]` — this block is written only after the artifacts exist.

Replace the `## Stage Progress` block with (preserve the actual stage names/dates already recorded for earlier stages; mark Vision Document Generation complete):

```markdown
## Stage Progress
### 🟣 DISCOVERY PHASE
- [x] Envision
- [x] Prototype & Validation (or skipped)
- [x] Product Strategy
- [x] Go-to-Market
- [x] Vision Document Generation
```

Replace (or add, if absent) the `## Handoff Artifacts` block with exactly:

```markdown
## Handoff Artifacts
- [x] discovery-document.md (full Discovery record)
- [x] vision-document.md (AI-DLC Inception input)
```

### Step 7: Log

- Log completion in `aiplc-docs/audit.md` with timestamp.
