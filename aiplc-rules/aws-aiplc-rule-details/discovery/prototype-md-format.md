# PROTOTYPE-{use-case}.md File Format

## Purpose
Define the standard format for PROTOTYPE-{use-case}.md files that contain all context needed to build prototypes.

## File Naming Convention

**Pattern**: `PROTOTYPE-{use-case-slug}.md`

Where `{use-case-slug}` is the kebab-case version of the use case name.

**Examples**:
- Use Case: "Customer Support Agent" → `PROTOTYPE-customer-support-agent.md`
- Use Case: "Sales Assistant" → `PROTOTYPE-sales-assistant.md`
- Use Case: "Invoice Processing Agent" → `PROTOTYPE-invoice-processing-agent.md`

## File Location

`aiplc-docs/discovery/prototypes/{use-case-slug}/PROTOTYPE-{use-case-slug}.md`

## Template for Agentic Use Cases

```markdown
# PROTOTYPE-{use-case-slug}.md

# {Use Case Name} - Prototype Specification

**Use Case**: {Use Case Name}
**Type**: Agentic
**Priority Score**: {X.X}/10 (if from prioritization)
**Generated**: {YYYY-MM-DD}

---

## Use Case Overview

### Problem Statement
{What problem does this agent solve?}

### Target Users
{Who will use this agent?}
- {Persona 1}
- {Persona 2}

### Business Value
{Why is this valuable?}
- {Value point 1}
- {Value point 2}
- {Value point 3}

### Success Criteria
{How will we know this prototype is successful?}
- {Criterion 1}
- {Criterion 2}

---

## Agent Requirements

### Purpose
{What does this agent do? One clear sentence.}

### LLM Configuration
- **Provider**: {Bedrock/Anthropic/OpenAI/Gemini/Other or "Not specified"}
- **Model**: {Specific model or "Claude 3.5 Sonnet (default)"}
- **Temperature**: {0.0-1.0 or "Default (0.7)"}
- **Max Tokens**: {Number or "Default (4096)"}

### Conversation Style
{How should the agent communicate?}
- Tone: {Formal/Casual/Professional/Friendly}
- Personality: {Brief description}
- Language: {English/Other}

---

## Tools (1-2 Simple Tools for Prototype)

### Tool 1: {Tool Name}

**Purpose**: {What does this tool do?}

**Implementation**: {Brief description of how it works}

**Input Parameters**:
- `{param1}`: {description}
- `{param2}`: {description}

**Output Format**:
```json
{
  "result": "...",
  "status": "success"
}
```

**Sample Usage**:
```
User: "{sample user request}"
Agent calls: tool_name(param1="value1", param2="value2")
Tool returns: {sample output}
Agent responds: "{sample agent response}"
```

### Tool 2: {Tool Name}
{Same structure as Tool 1}

---

## Frontend Requirements

### Device Target
{Mobile/Desktop/Both}

### Key Screens/Views
1. **{Screen 1 Name}**: {Description}
2. **{Screen 2 Name}**: {Description}
3. **{Screen 3 Name}**: {Description}

### User Flow
{Brief description of main user journey}
1. User opens app/page
2. User {action}
3. Agent {response}
4. User sees {result}

### UI Components Needed
- {Component 1} (e.g., Chat interface)
- {Component 2} (e.g., Message bubbles)
- {Component 3} (e.g., Input field)
- {Component 4} (e.g., Tool result display)

---

## Design Context

### Brand Reference
**URL**: {https://example.com or "Generic modern design"}

### Style Guidelines
{If brand URL provided, extract these; otherwise use defaults}
- **Primary Color**: {#hex or "Default blue"}
- **Secondary Color**: {#hex or "Default gray"}
- **Font Family**: {Font name or "System default"}
- **Logo**: {URL or location or "None"}

### Design Notes
{Any specific design requirements or preferences}

---

## Sample Interactions

### Interaction 1: {Scenario Name}
**User**: "{User message}"
**Agent**: "{Agent response}"
**Tools Used**: {Tool name(s) or "None"}
**Expected Outcome**: {What should happen}

### Interaction 2: {Scenario Name}
{Same structure}

### Interaction 3: {Scenario Name}
{Same structure}

---

## Deployment

### Local Development
- **Port**: {3000 or other}
- **URL**: http://localhost:{port}
- **Hot Reload**: {Yes/No}

### Dependencies
{List any specific dependencies or requirements}
- {Dependency 1}
- {Dependency 2}

### Environment Variables Needed
{If any specific env vars required}
- `{VAR_NAME}`: {Description}

---

## Testing & Validation

### Test Scenarios
1. {Test scenario 1}
2. {Test scenario 2}
3. {Test scenario 3}

### Acceptance Criteria
- [ ] {Criterion 1}
- [ ] {Criterion 2}
- [ ] {Criterion 3}

---

## Notes

### Assumptions
{Any assumptions made during specification}

### Constraints
{Any known constraints or limitations}

### Future Enhancements
{Ideas for future iterations - not for this prototype}
- {Enhancement 1}
- {Enhancement 2}

---

## Metadata

**Created By**: {AI-PLC Workflow}
**Source**: {Path A - PR/FAQ / Path B - Use Case Intake}
**Prioritization Rank**: {Rank if applicable}
**Related Documents**:
- Use Case Intake: {link if applicable}
- Prioritization: {link if applicable}
- PR/FAQ: {link if applicable}
```

## Template for Application Use Cases

```markdown
# PROTOTYPE-{use-case-slug}.md

# {Use Case Name} - Prototype Specification

**Use Case**: {Use Case Name}
**Type**: Application
**Priority Score**: {X.X}/10 (if from prioritization)
**Generated**: {YYYY-MM-DD}

---

## Use Case Overview

### Problem Statement
{What problem does this application solve?}

### Target Users
{Who will use this application?}
- {Persona 1}
- {Persona 2}

### Business Value
{Why is this valuable?}
- {Value point 1}
- {Value point 2}
- {Value point 3}

### Success Criteria
{How will we know this prototype is successful?}
- {Criterion 1}
- {Criterion 2}

---

## Application Requirements

### Purpose
{What does this application do? One clear sentence.}

### Core Features (2-3 for Prototype)

#### Feature 1: {Feature Name}
**Description**: {What it does}
**User Story**: As a {user}, I want to {action} so that {benefit}
**Acceptance Criteria**:
- {Criterion 1}
- {Criterion 2}

#### Feature 2: {Feature Name}
{Same structure}

#### Feature 3: {Feature Name}
{Same structure}

### Technology Stack
- **Frontend**: {React/Vue/Plain HTML/Other or "Default (React)"}
- **Backend**: {Node/Python/Other or "Default (Node.js)"}
- **Database**: {If needed or "None for prototype"}
- **APIs**: {Any external APIs needed}

---

## Frontend Requirements

### Device Target
{Mobile/Desktop/Both}

### Key Screens/Views
1. **{Screen 1 Name}**: {Description}
   - Components: {list}
   - Actions: {list}

2. **{Screen 2 Name}**: {Description}
   - Components: {list}
   - Actions: {list}

3. **{Screen 3 Name}**: {Description}
   - Components: {list}
   - Actions: {list}

### User Flow
{Brief description of main user journey}
1. User {action}
2. System {response}
3. User sees {result}

### UI Components Needed
- {Component 1}
- {Component 2}
- {Component 3}

---

## Design Context

### Brand Reference
**URL**: {https://example.com or "Generic modern design"}

### Style Guidelines
{If brand URL provided, extract these; otherwise use defaults}
- **Primary Color**: {#hex or "Default blue"}
- **Secondary Color**: {#hex or "Default gray"}
- **Font Family**: {Font name or "System default"}
- **Logo**: {URL or location or "None"}

### Design Notes
{Any specific design requirements or preferences}

---

## Data & Integration

### Data Model (Simplified for Prototype)
{If applicable}
```
Entity: {Name}
- field1: {type}
- field2: {type}
```

### Mock Data
{Description of demo data needed}
- {Data set 1}
- {Data set 2}

### External Integrations
{If any APIs or services needed}
- {Integration 1}: {Purpose}
- {Integration 2}: {Purpose}

---

## Sample User Scenarios

### Scenario 1: {Scenario Name}
**Steps**:
1. User {action}
2. System {response}
3. User sees {result}

**Expected Outcome**: {What should happen}

### Scenario 2: {Scenario Name}
{Same structure}

### Scenario 3: {Scenario Name}
{Same structure}

---

## Deployment

### Local Development
- **Port**: {3000 or other}
- **URL**: http://localhost:{port}
- **Hot Reload**: {Yes/No}

### Dependencies
{List any specific dependencies or requirements}
- {Dependency 1}
- {Dependency 2}

### Environment Variables Needed
{If any specific env vars required}
- `{VAR_NAME}`: {Description}

---

## Testing & Validation

### Test Scenarios
1. {Test scenario 1}
2. {Test scenario 2}
3. {Test scenario 3}

### Acceptance Criteria
- [ ] {Criterion 1}
- [ ] {Criterion 2}
- [ ] {Criterion 3}

---

## Notes

### Assumptions
{Any assumptions made during specification}

### Constraints
{Any known constraints or limitations}

### Future Enhancements
{Ideas for future iterations - not for this prototype}
- {Enhancement 1}
- {Enhancement 2}

---

## Metadata

**Created By**: {AI-PLC Workflow}
**Source**: {Path A - PR/FAQ / Path B - Use Case Intake}
**Prioritization Rank**: {Rank if applicable}
**Related Documents**:
- Use Case Intake: {link if applicable}
- Prioritization: {link if applicable}
- PR/FAQ: {link if applicable}
```

## Required vs Optional Sections

### REQUIRED (Must be present):
- Use Case Overview
- {Agent/Application} Requirements
- Frontend Requirements (at least device target)
- Deployment (at least port)

### OPTIONAL (Can use defaults):
- LLM Configuration (will ask during building)
- Design Context (can use generic design)
- Sample Interactions/Scenarios (helpful but not blocking)
- Testing & Validation (can be added during building)
- Notes section

## Usage Notes

1. **Portability**: These files should be self-contained and shareable
2. **Clarity**: Anyone reading the file should understand what to build
3. **Completeness**: Include enough detail to build without asking many questions
4. **Flexibility**: Allow for defaults where specific details aren't critical
5. **Workshop-Ready**: Teams can take these files and build independently
