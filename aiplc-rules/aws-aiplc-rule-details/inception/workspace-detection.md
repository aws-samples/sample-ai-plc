# Workspace Detection

**Purpose**: Determine workspace state and check for existing AI-PLC projects

## Step 0: Check for Existing PROTOTYPE-*.md Files (PRIORITY CHECK)

**BEFORE any other checks**, scan for existing prototype specification files:

**Path pattern**: `aiplc-docs/discovery/prototypes/*/PROTOTYPE-*.md`

### IF PROTOTYPE-*.md file(s) found:

This is **Entry Point 1** - Build from existing prototype specifications.

**Typical scenario**: Workshop environment where teams receive pre-generated PROTOTYPE-*.md files.

1. Count the files found
2. Extract use case names from filenames
3. Present to user:

```
I found {N} prototype specification file(s) in your workspace:

1. 📄 PROTOTYPE-{use-case-1-slug}.md
2. 📄 PROTOTYPE-{use-case-2-slug}.md (if multiple)
[...]

These files contain complete specifications for building prototypes.

I'll skip the discovery phase and build prototypes directly from 
these specifications.
```

4. **SKIP ALL DISCOVERY PHASES**:
   - Skip pain point analysis
   - Skip PR/FAQ generation
   - Skip use case intake
   - Skip prioritization
   - Skip context generation

5. **JUMP DIRECTLY TO**: Prototype Building stage (see `discovery/prototype-building.md`)

6. After prototypes built, continue to Product Strategy → GTM

**STOP HERE** - Do not proceed with Steps 1-6 below if PROTOTYPE-*.md files found.

---

### IF NO PROTOTYPE-*.md files found:

Continue with normal workspace detection (Steps 1-6 below).

---

## Step 1: Check for Existing AI-PLC Project

Check if `aiplc-docs/aiplc-state.md` exists:
- **If exists**: Resume from last phase (load context from previous phases)
- **If not exists**: Continue with new project assessment

## Step 2: Scan Workspace for Existing Code

**Determine if workspace has existing code:**
- Scan workspace for source code files (.java, .py, .js, .ts, .jsx, .tsx, .kt, .kts, .scala, .groovy, .go, .rs, .rb, .php, .c, .h, .cpp, .hpp, .cc, .cs, .fs, etc.)
- Check for build files (pom.xml, package.json, build.gradle, etc.)
- Look for project structure indicators
- Identify workspace root directory (NOT aiplc-docs/)

**Record findings:**
```markdown
## Workspace State
- **Existing Code**: [Yes/No]
- **Programming Languages**: [List if found]
- **Build System**: [Maven/Gradle/npm/etc. if found]
- **Project Structure**: [Monolith/Microservices/Library/Empty]
- **Workspace Root**: [Absolute path]
```

## Step 3: Determine Next Phase

**IF workspace is empty (no existing code)**:
- Set flag: `brownfield = false`
- Check for existing Discovery artifacts in `aiplc-docs/discovery/`
- **IF Discovery artifacts exist**: Load them, skip to Requirements Analysis
- **IF no Discovery artifacts**: Next phase is DISCOVERY PHASE
  - Present Discovery Mode Selection (see `discovery/discovery-mode-selection.md`)
  - User chooses: [A] Pain points → PR/FAQ OR [B] Use cases

**IF workspace has existing code**:
- Set flag: `brownfield = true`
- Check for existing reverse engineering artifacts in `aiplc-docs/inception/reverse-engineering/`
- **IF reverse engineering artifacts exist**: Load them, skip to Requirements Analysis
- **IF no reverse engineering artifacts**: Next phase is Reverse Engineering

## Step 4: Create Initial State File

Create `aiplc-docs/aiplc-state.md`:

```markdown
# AI-PLC State Tracking

## Project Information
- **Project Type**: [Greenfield/Brownfield]
- **Start Date**: [ISO timestamp]
- **Current Stage**: INCEPTION - Workspace Detection

## Workspace State
- **Existing Code**: [Yes/No]
- **Reverse Engineering Needed**: [Yes/No]
- **Workspace Root**: [Absolute path]

## Code Location Rules
- **Application Code**: Workspace root (NEVER in aiplc-docs/)
- **Documentation**: aiplc-docs/ only
- **Structure patterns**: See code-generation.md Critical Rules

## Stage Progress
[Will be populated as workflow progresses]
```

## Step 5: Present Completion Message

**For Brownfield Projects:**
```markdown
# 🔍 Workspace Detection Complete

Workspace analysis findings:
• **Project Type**: Brownfield project
• [AI-generated summary of workspace findings in bullet points]
• **Next Step**: Proceeding to **Reverse Engineering** to analyze existing codebase...
```

**For Greenfield Projects:**
```markdown
# 🔍 Workspace Detection Complete

Workspace analysis findings:
• **Project Type**: Greenfield project
• **Next Step**: Proceeding to **Discovery Mode Selection** to determine how to start (pain points or use cases)...
```

## Step 6: Automatically Proceed

- **No user approval required** - this is informational only
- Automatically proceed to next phase:
  - **If PROTOTYPE-*.md found**: Prototype Building (Entry Point 1)
  - **Brownfield**: Reverse Engineering (if no existing artifacts) or Requirements Analysis (if artifacts exist)
  - **Greenfield**: Discovery Mode Selection → User chooses Path A (Envision) or Path B (Use Case Intake)
