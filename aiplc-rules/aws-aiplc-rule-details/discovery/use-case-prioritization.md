# Use Case Prioritization

## Purpose
Prioritize all use cases and select top 3 for prototype development.

## When to Execute
- After Use Case Intake completes
- When multiple solutions identified from PR/FAQ

## Prioritization Frameworks

### Framework 1: Agentic Use Cases

Criteria for agentic use cases:

1. **Business Value** (0-10)
   - Revenue impact
   - Cost savings
   - User satisfaction improvement

2. **LLM Capability Match** (0-10)
   - Can current LLMs handle this well?
   - Complexity of reasoning required
   - Quality of expected outputs

3. **Tool Availability** (0-10)
   - Are required tools/APIs available?
   - Ease of tool integration
   - Data accessibility

4. **User Acceptance** (0-10)
   - Will users trust an agent for this?
   - Change management complexity
   - User experience expectations

5. **Time to Market** (0-10)
   - Development effort
   - Dependencies
   - Resource availability

6. **Strategic Alignment** (0-10)
   - Company priorities
   - Market differentiation
   - Competitive advantage

**Weighted Score Calculation**:
- Business Value: 25%
- LLM Capability Match: 20%
- Tool Availability: 15%
- User Acceptance: 15%
- Time to Market: 15%
- Strategic Alignment: 10%

### Framework 2: Application Use Cases

Criteria for application use cases:

1. **Business Value** (0-10)
   - Revenue impact
   - Cost savings
   - User satisfaction

2. **Technical Feasibility** (0-10)
   - Technology maturity
   - Team expertise
   - Infrastructure readiness

3. **User Impact** (0-10)
   - Number of users affected
   - Frequency of use
   - Critical to workflow?

4. **Development Effort** (0-10, inverse)
   - Complexity
   - Team size needed
   - Timeline

5. **Integration Complexity** (0-10, inverse)
   - Number of systems to integrate
   - API availability
   - Data migration needs

6. **Strategic Alignment** (0-10)
   - Company priorities
   - Market needs
   - Competitive positioning

**Weighted Score Calculation**:
- Business Value: 25%
- Technical Feasibility: 20%
- User Impact: 20%
- Development Effort: 15%
- Integration Complexity: 10%
- Strategic Alignment: 10%

## Step 1: Apply Frameworks

For each use case:
1. Apply appropriate framework (agentic or application)
2. Score each criterion
3. Calculate weighted total score
4. Document rationale for each score

## Step 2: Generate Rankings

Create separate rankings:
- **Agentic Use Cases**: Ranked by score (highest to lowest)
- **Application Use Cases**: Ranked by score (highest to lowest)

## Step 3: Present Rankings to User

```
Use Case Prioritization Results:

AGENTIC USE CASES ({X} total):

Rank | Use Case Name              | Score | Key Strengths
-----|----------------------------|-------|------------------
1    | {Name}                     | {9.2} | {High value, low complexity}
2    | {Name}                     | {8.8} | {Clear ROI, good tools}
3    | {Name}                     | {8.5} | {Strategic priority}
4    | {Name}                     | {8.2} | {User demand}
[Continue for all agentic use cases]

APPLICATION USE CASES ({Y} total):

Rank | Use Case Name              | Score | Key Strengths
-----|----------------------------|-------|------------------
1    | {Name}                     | {9.0} | {High impact, feasible}
2    | {Name}                     | {8.5} | {Quick win}
3    | {Name}                     | {8.2} | {Strategic fit}
[Continue for all application use cases]

RECOMMENDATION:
Based on the scoring, I recommend prototyping the top 3 use cases:

1. {Top Use Case 1} - Score: {X.X} - {Type}
2. {Top Use Case 2} - Score: {X.X} - {Type}
3. {Top Use Case 3} - Score: {X.X} - {Type}

These represent the best balance of value, feasibility, and strategic fit.

Do you agree with this selection?

[A] Yes, proceed with these top 3
[B] No, I want to adjust the selection (specify which use cases)

[Answer]:
```

## Step 4: Handle User Response

### If [A] - Agree with top 3:
- Confirm selection
- Proceed to Prototype Context Generation

### If [B] - Adjust selection:

Ask:
```
Which use cases would you like to prototype instead?
(Select 3 use cases by name or rank number)

Your selection:
```

Confirm adjusted selection:
```
You've selected:
1. {Use Case Name}
2. {Use Case Name}
3. {Use Case Name}

Proceed with these 3 use cases?

[A] Yes
[B] No, let me adjust again

[Answer]:
```

## Step 5: Document Prioritization

Create files:

### File 1: `aiplc-docs/discovery/prioritization/framework.md`

```markdown
# Prioritization Framework

**Date**: {timestamp}
**Use Cases Evaluated**: {N}

## Frameworks Used

### Agentic Use Case Framework
[Document criteria and weights]

### Application Use Case Framework
[Document criteria and weights]
```

### File 2: `aiplc-docs/discovery/prioritization/scoring.md`

```markdown
# Use Case Scoring Details

## Agentic Use Cases

### {Use Case Name}
- Business Value: {score}/10 - {rationale}
- LLM Capability Match: {score}/10 - {rationale}
- Tool Availability: {score}/10 - {rationale}
- User Acceptance: {score}/10 - {rationale}
- Time to Market: {score}/10 - {rationale}
- Strategic Alignment: {score}/10 - {rationale}
- **Total Weighted Score**: {X.X}/10

[Repeat for each use case]

## Application Use Cases
[Same structure]
```

### File 3: `aiplc-docs/discovery/prioritization/ranking.md`

```markdown
# Final Use Case Rankings

**Date**: {timestamp}

## Agentic Use Cases (Ranked)
1. {Name} - Score: {X.X}
2. {Name} - Score: {X.X}
[...]

## Application Use Cases (Ranked)
1. {Name} - Score: {X.X}
2. {Name} - Score: {X.X}
[...]

## Selected for Prototyping (Top 3)
1. {Name} - Score: {X.X} - {Type}
2. {Name} - Score: {X.X} - {Type}
3. {Name} - Score: {X.X} - {Type}

## Rationale
{Why these 3 were selected}
```

## Audit Logging

```markdown
## Use Case Prioritization
**Timestamp**: [ISO timestamp]
**User Input**: "[User's selection confirmation]"
**AI Response**: "Prioritized {N} use cases. Selected top 3: {names}. Proceeding to prototype context generation."
**Context**: Use case prioritization complete
```

## Next Steps

Proceed to: `prototype-context-generation.md`
