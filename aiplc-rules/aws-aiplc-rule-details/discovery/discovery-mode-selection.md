# Discovery Mode Selection

## Purpose
Determine how to start the Discovery phase based on user's situation.

## When to Execute
- ONLY if NO PROTOTYPE-*.md files found in workspace
- This is the first question after workspace detection
- Executed before any other Discovery activities

## Decision Point

Ask the user:

```
How would you like to start Discovery?

[A] Start from customer pain points (create PR/FAQ)
[B] I already have use cases to prioritize

[Answer]:
```

## Path Selection Logic

### IF User selects [A] - Pain Points Path
- Proceed to: `envision.md`
- This path will:
  1. Gather customer pain points
  2. Generate PR/FAQ
  3. Analyze PR/FAQ for solutions (single or multiple)
  4. Branch accordingly

### IF User selects [B] - Use Cases Path
- Proceed to: `use-case-intake.md`
- This path will:
  1. Gather all N use cases from user
  2. Prioritize use cases
  3. Select top 3 for prototyping
  4. Generate PROTOTYPE-*.md files

## Audit Logging

Log the user's choice:

```markdown
## Discovery Mode Selection
**Timestamp**: [ISO timestamp]
**User Input**: "[Complete raw user input]"
**AI Response**: "User selected [Path A/Path B]. Proceeding to [next stage]."
**Context**: Discovery mode selection
```

## Next Steps

- Path A → `envision.md`
- Path B → `use-case-intake.md`
