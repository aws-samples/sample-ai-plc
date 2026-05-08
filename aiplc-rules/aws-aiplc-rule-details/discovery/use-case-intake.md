# Use Case Intake

## Purpose
Gather and document all use cases from the user for prioritization.

## When to Execute
- Path B: User selected "I already have use cases" in discovery mode selection
- Path A.2: Multiple solutions identified from PR/FAQ analysis

## Step 1: Determine Number of Use Cases

Ask:

```
How many use cases do you have?

Your answer:
```

Record the number: N use cases

## Step 2: Gather Use Case Details

For each use case (1 to N), ask:

```
Use Case {X} of {N}:

Please provide the following information:

1. Use Case Name:
2. Brief Description (what problem does it solve?):
3. Target Users/Personas:
4. Business Value (High/Medium/Low):
5. Technical Complexity (High/Medium/Low):
6. Type (Agentic or Application):
7. Key Capabilities Needed (list 2-3):
8. Any Constraints or Dependencies:

You can provide all details at once or answer each question separately.
```

### Flexible Input Formats

Accept use cases in various formats:
- Structured responses to each question
- Bulk paste of all use cases
- Table format
- Conversational description

If user provides bulk input, parse and extract details, then confirm:

```
I've captured the following use cases:

1. {Use Case 1 Name} - {Type}
   {Brief summary}

2. {Use Case 2 Name} - {Type}
   {Brief summary}

[Continue for all N]

Is this correct? Would you like to add or modify any details?

[A] Correct, proceed
[B] I need to update some details

[Answer]:
```

## Step 3: Categorize Use Cases

Automatically categorize:
- **Agentic**: {count} use cases
- **Application**: {count} use cases

Present summary:

```
Use Case Summary:

Total: {N} use cases
- Agentic: {X} use cases
- Application: {Y} use cases

Agentic Use Cases:
1. {Name}
2. {Name}
[...]

Application Use Cases:
1. {Name}
2. {Name}
[...]

Ready to proceed to prioritization?

[A] Yes, prioritize these use cases
[B] No, I need to add/modify use cases

[Answer]:
```

## Step 4: Document Use Cases

Create file: `aiplc-docs/discovery/use-case-intake/use-cases.md`

```markdown
# Use Case Intake

**Date**: {timestamp}
**Total Use Cases**: {N}
**Source**: {Path B - Direct input OR Path A.2 - From PR/FAQ}

## Use Case List

### Agentic Use Cases ({X} total)

#### 1. {Use Case Name}
- **Description**: {description}
- **Target Users**: {users}
- **Business Value**: {High/Medium/Low}
- **Technical Complexity**: {High/Medium/Low}
- **Key Capabilities**: 
  - {capability 1}
  - {capability 2}
  - {capability 3}
- **Constraints**: {constraints if any}

[Repeat for each agentic use case]

### Application Use Cases ({Y} total)

#### 1. {Use Case Name}
[Same structure as above]

[Repeat for each application use case]

## Next Steps
Proceed to Use Case Prioritization
```

## Audit Logging

```markdown
## Use Case Intake
**Timestamp**: [ISO timestamp]
**User Input**: "[Complete raw user input for all use cases]"
**AI Response**: "Captured {N} use cases ({X} agentic, {Y} application). Proceeding to prioritization."
**Context**: Use case intake complete
```

## Next Steps

Proceed to: `use-case-prioritization.md`
