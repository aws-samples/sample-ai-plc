# Solution Analysis

## Purpose
Analyze the PR/FAQ to determine if it describes a single solution or multiple solution options.

## When to Execute
- ONLY after Envision stage completes (Path A)
- After PR/FAQ has been generated and approved
- Before deciding on prototype approach

## Analysis Process

### Step 1: Analyze PR/FAQ Content

Read the approved PR/FAQ and identify:
- How many distinct solutions are described?
- Are there multiple approaches to solving the pain points?
- Does the PR/FAQ suggest alternatives or options?

### Step 2: Categorize Solutions

For each identified solution, determine:
- **Type**: Agentic or Application
- **Scope**: Standalone or integrated
- **Complexity**: Simple, Medium, Complex

### Step 3: Make Determination

**SINGLE SOLUTION** if:
- PR/FAQ describes one clear approach
- No alternatives or options mentioned
- Focused on one product/service

**MULTIPLE SOLUTIONS** if:
- PR/FAQ mentions multiple approaches
- Different options to address pain points
- Could be solved in different ways

## Branching Logic

### Branch A.1: Single Solution Identified

Present to user:

```
Based on the PR/FAQ, I've identified a single, clear solution:

{Solution Name} - {Agentic/Application}
{Brief description}

This solution addresses the pain points by:
- {Key capability 1}
- {Key capability 2}
- {Key capability 3}

I'll proceed to prototype this solution.

Continue to prototype? [Yes/No]
```

If Yes → Proceed to `prototype-validation.md` (existing single prototype flow)

### Branch A.2: Multiple Solutions Identified

Present to user:

```
Based on the PR/FAQ analysis, I've identified N potential solutions 
to address the customer pain points:

1. {Solution 1 Name} - {Agentic/Application}
   {Brief description}

2. {Solution 2 Name} - {Agentic/Application}
   {Brief description}

3. {Solution 3 Name} - {Agentic/Application}
   {Brief description}

[Continue for all N solutions]

These solutions include:
- {X} agentic use cases
- {Y} application use cases

Would you like to prioritize these and prototype the top 3?

[A] Yes, prioritize and prototype top 3
[B] No, focus on just one solution (specify which)

[Answer]:
```

If [A] → Proceed to `use-case-prioritization.md`
If [B] → Ask which solution, then proceed to `prototype-validation.md`

## Document Solutions

Create file: `aiplc-docs/discovery/solution-analysis/identified-solutions.md`

```markdown
# Identified Solutions from PR/FAQ

**Analysis Date**: {timestamp}
**PR/FAQ**: See envision/prfaq.md

## Solutions Identified

### Solution 1: {Name}
- **Type**: {Agentic/Application}
- **Description**: {description}
- **Addresses Pain Points**: {list}
- **Key Capabilities**: {list}

### Solution 2: {Name}
[Repeat for each solution]

## Recommendation
{Single solution or Multiple solutions requiring prioritization}

## Next Steps
{Path A.1 or Path A.2}
```

## Audit Logging

```markdown
## Solution Analysis
**Timestamp**: [ISO timestamp]
**User Input**: "[User's response to branching question]"
**AI Response**: "Identified {N} solutions. Proceeding to {next stage}."
**Context**: Solution analysis from PR/FAQ
```

## Next Steps

- Single Solution → `prototype-validation.md`
- Multiple Solutions → `use-case-prioritization.md`
