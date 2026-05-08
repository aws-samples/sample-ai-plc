# Prototype Context Generation

## Purpose
Generate PROTOTYPE-{use-case}.md files for the top 3 selected use cases. These files contain all context needed for building prototypes.

## When to Execute
- After Use Case Prioritization completes
- Top 3 use cases have been selected

## Overview

For each of the 3 selected use cases, gather detailed context and generate a comprehensive PROTOTYPE-{use-case}.md file that can be:
- Used immediately to build prototypes in this session
- Shared with other teams for parallel prototype development
- Used in future sessions to build prototypes

## Step 1: Announce Context Generation

```
I'll now generate detailed prototype specifications for the top 3 use cases:

1. {Use Case 1 Name}
2. {Use Case 2 Name}
3. {Use Case 3 Name}

For each use case, I'll gather:
- Design context (brand, look & feel)
- Technical requirements (LLM, tools, etc.)
- Frontend specifications
- Deployment details

This will create PROTOTYPE-{use-case}.md files that contain everything 
needed to build the prototypes.

Let's start with Use Case 1: {Name}
```

## Step 2: For Each Use Case, Gather Context

### Context Questions (Per Use Case)

#### Question 1: Brand & Design Context

```
For {Use Case Name}:

What's your company/product website URL for brand matching?
(The prototype will match the look and feel of this site)

Your answer:
```

If no URL provided, ask:
```
Would you like to:
[A] Describe the brand style (colors, tone, etc.)
[B] Use a generic modern design

[Answer]:
```

#### Question 2: Device Target (if not already specified)

```
What device(s) should this prototype target?

[A] Mobile (smartphone)
[B] Desktop (web browser)
[C] Both (responsive design)

[Answer]:
```

#### Question 3: Tools/Features (for Agentic use cases)

```
For the {Use Case Name} agent, what 1-2 simple tools should it have?
(These are for demonstration purposes - keep them simple)

Examples:
- FAQ lookup
- Database query
- API call
- File search
- Calculation

Your answer:
```

#### Question 4: Key Screens/Views (for Application use cases)

```
For the {Use Case Name} application, what are the key screens?
(List 2-3 main screens for the prototype)

Examples:
- Dashboard
- List view
- Detail view
- Form
- Settings

Your answer:
```

#### Question 5: Sample Interactions (for Agentic use cases)

```
Describe 2-3 sample interactions users might have with this agent.

Example format:
1. User asks: "..." → Agent responds: "..."
2. User asks: "..." → Agent responds: "..."

Your answer:
```

## Step 3: Generate PROTOTYPE-{use-case}.md File

For each use case, create the file following the template in `prototype-md-format.md`.

File location: `aiplc-docs/discovery/prototypes/{use-case-slug}/PROTOTYPE-{use-case-slug}.md`

Where `{use-case-slug}` is the kebab-case version of the use case name.

Example:
- Use Case: "Customer Support Agent"
- Slug: "customer-support-agent"
- File: `aiplc-docs/discovery/prototypes/customer-support-agent/PROTOTYPE-customer-support-agent.md`

## Step 4: Present Completion for Each Use Case

After generating each PROTOTYPE-*.md file:

```
✅ Generated PROTOTYPE-{use-case-slug}.md

This file contains:
- Use case overview
- {Agentic/Application} requirements
- {Tools/Features} specifications
- Design context ({brand reference})
- Frontend requirements ({device target})
- Sample interactions
- Deployment instructions

File location: aiplc-docs/discovery/prototypes/{use-case-slug}/PROTOTYPE-{use-case-slug}.md

Moving to Use Case 2: {Name}...
```

## Step 5: Present Final Summary

After all 3 PROTOTYPE-*.md files are generated:

```
✅ Prototype Context Generation Complete

I've generated 3 prototype specification files:

1. 📄 PROTOTYPE-{use-case-1-slug}.md
   Location: aiplc-docs/discovery/prototypes/{use-case-1-slug}/
   Type: {Agentic/Application}

2. 📄 PROTOTYPE-{use-case-2-slug}.md
   Location: aiplc-docs/discovery/prototypes/{use-case-2-slug}/
   Type: {Agentic/Application}

3. 📄 PROTOTYPE-{use-case-3-slug}.md
   Location: aiplc-docs/discovery/prototypes/{use-case-3-slug}/
   Type: {Agentic/Application}

These files contain complete specifications for building prototypes.

What would you like to do next?

[A] Build all 3 prototypes now (in this session)
[B] Stop here - I'll share these files with teams to build prototypes separately
[C] Build only specific prototypes (specify which)

[Answer]:
```

## Step 6: Handle User Decision

### If [A] - Build all 3 now:
- Proceed to `prototype-building.md`
- Build all 3 prototypes sequentially

### If [B] - Stop here (handoff mode):
- Confirm files are ready for sharing
- Optionally continue to Product Strategy for one use case
- End Discovery phase

### If [C] - Build specific prototypes:
- Ask which ones to build
- Proceed to `prototype-building.md` for selected ones

## Additional Context Files

For each use case, also create:

### File: `design-context.md`
```markdown
# Design Context - {Use Case Name}

**Brand Reference**: {URL or description}
**Device Target**: {Mobile/Desktop/Both}
**Style Notes**: {Any specific design requirements}
**Color Palette**: {If extracted from brand URL}
**Typography**: {If specified}
```

### File: `iteration-log.md`
```markdown
# Iteration Log - {Use Case Name}

This file will track iterations made to the prototype during building and validation.

## Iterations
(To be populated during prototype building)
```

## Audit Logging

```markdown
## Prototype Context Generation
**Timestamp**: [ISO timestamp]
**User Input**: "[User's answers to all context questions]"
**AI Response**: "Generated 3 PROTOTYPE-*.md files. User chose: {A/B/C}."
**Context**: Prototype context generation complete

---

## Prototype Context Generation - Use Case 1
**Timestamp**: [ISO timestamp]
**Use Case**: {Name}
**User Input**: "[Answers for this use case]"
**AI Response**: "Generated PROTOTYPE-{slug}.md"
**Context**: Context gathered for use case 1

[Repeat for each use case]
```

## Next Steps

- If [A] → `prototype-building.md`
- If [B] → Optional: Product Strategy, then end
- If [C] → `prototype-building.md` (for selected use cases)
