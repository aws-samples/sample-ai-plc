# AI-PLC Discovery Phase Overview

**Purpose**: Technical reference for AI model and Product Managers to understand the Discovery workflow structure.

**Note**: This workspace is exclusively for the Discovery phase. Inception, Construction, and Operations phases happen in a separate developer workspace.

## Discovery Phase Only:
• **DISCOVERY PHASE**: PM-led product definition with 3 entry points
  - Entry Point 1: Existing PROTOTYPE-*.md files → Jump to Prototype Building
  - Entry Point 2: Pain points → PR/FAQ → Solution Analysis → Prototyping
  - Entry Point 3: Use cases → Prioritization → Prototype Context Generation → Prototyping
• **Output**: Discovery Document for developer handoff

## The Discovery Workflow:
• **Workspace Detection** (always) → **Check for PROTOTYPE-*.md** (priority) → **DISCOVERY PHASE** (3 entry points) → **Product Strategy** → **Go-to-Market** → **Discovery Document Complete**

## Discovery Phase Entry Points:
• **Entry Point 1 (Highest Priority)**: PROTOTYPE-*.md files exist → Skip all discovery → Build prototypes directly
• **Entry Point 2 (Path A)**: No PROTOTYPE-*.md → User chooses pain points → Envision → Solution Analysis → Single or Multiple solutions
• **Entry Point 3 (Path B)**: No PROTOTYPE-*.md → User chooses use cases → Use Case Intake → Prioritization → Prototype Context Generation

## How It Works:
• **AI analyzes** your workspace to determine which entry point to use
• **Discovery Phase stages**: Workspace Detection (always), then one of three paths based on situation
• **Output**: Discovery Document containing pain points/use cases, PROTOTYPE-*.md files, Product Strategy, and Go-to-Market plan
• **Handoff**: Developers use Discovery Document in their workspace for Inception, Construction, and Operations phases

## Your Role as Product Manager:
• **Answer questions** in dedicated question files using [Answer]: tags with letter choices (A, B, C, D, E)
• **Option E available**: Choose "Other" and describe your custom response if provided options don't match
• **Review and approve** each Discovery stage before proceeding
• **Make product decisions** on strategy, positioning, and go-to-market
• **Important**: Focus on product vision - technical implementation happens in developer workspace

## AI-PLC Discovery Phase Workflow:

```mermaid
flowchart TD
    Start(["PM Request"])
    
    WD["Workspace Detection"]
    PROTO_CHECK{"PROTOTYPE-*.md<br/>files exist?"}
    
    subgraph DISCOVERY["🟣 DISCOVERY PHASE (PM-Led)"]
        DMS["Discovery Mode<br/>Selection"]
        ENV["Envision<br/>(Path A)"]
        SOL["Solution Analysis"]
        UCI["Use Case Intake<br/>(Path B)"]
        UCP["Use Case<br/>Prioritization"]
        PCG["Prototype Context<br/>Generation"]
        PB["Prototype Building"]
        PV["Prototype & Validation<br/>(Path A.1 - Single)"]
        PS["Product Strategy"]
        GTM["Go-to-Market"]
    end
    
    Complete(["Discovery Document<br/>Complete"])
    Handoff(["Hand off to<br/>Developers"])
    
    Start --> WD
    WD --> PROTO_CHECK
    
    PROTO_CHECK -->|Yes - Entry Point 1| PB
    PROTO_CHECK -->|No| DMS
    
    DMS -->|Path A: Pain Points| ENV
    DMS -->|Path B: Use Cases| UCI
    
    ENV --> SOL
    SOL -->|Single Solution| PV
    SOL -->|Multiple Solutions| UCP
    
    UCI --> UCP
    UCP --> PCG
    PCG --> PB
    
    PV --> PS
    PB --> PS
    PS --> GTM
    GTM --> Complete
    Complete --> Handoff
    
    style WD fill:#4CAF50,stroke:#1B5E20,stroke-width:3px,color:#fff
    style PROTO_CHECK fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,color:#000
    style DMS fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,color:#000
    style ENV fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,stroke-dasharray: 5 5,color:#000
    style SOL fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,stroke-dasharray: 5 5,color:#000
    style UCI fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,stroke-dasharray: 5 5,color:#000
    style UCP fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,stroke-dasharray: 5 5,color:#000
    style PCG fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,stroke-dasharray: 5 5,color:#000
    style PB fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,stroke-dasharray: 5 5,color:#000
    style PV fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,stroke-dasharray: 5 5,color:#000
    style PS fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,stroke-dasharray: 5 5,color:#000
    style GTM fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,stroke-dasharray: 5 5,color:#000
    style DISCOVERY fill:#E1BEE7,stroke:#6A1B9A,stroke-width:3px, color:#000
    style Start fill:#CE93D8,stroke:#6A1B9A,stroke-width:3px,color:#000
    style Complete fill:#4CAF50,stroke:#1B5E20,stroke-width:3px,color:#fff
    style Handoff fill:#4CAF50,stroke:#1B5E20,stroke-width:3px,color:#fff
    
    linkStyle default stroke:#333,stroke-width:2px
```

## Stage Descriptions:

### 🟣 DISCOVERY PHASE - PM-Led Product Definition

**Three Entry Points:**

#### Entry Point 1: Existing PROTOTYPE-*.md Files (Highest Priority)
- Workspace Detection finds PROTOTYPE-*.md files in workspace
- Skip all discovery phases (pain points, PR/FAQ, use case intake, prioritization)
- Jump directly to Prototype Building
- Typical scenario: Workshop environment where teams receive pre-generated specifications

#### Entry Point 2: Path A - Start from Pain Points
- Discovery Mode Selection: User chooses [A] Pain points
- Envision: Gather customer pain points, generate PR/FAQ using Working Backwards
- Solution Analysis: Determine single solution or multiple solutions
  - Single solution → Prototype & Validation (existing flow)
  - Multiple solutions → Use Case Prioritization → Prototype Context Generation
- Product Strategy: Positioning, differentiation, business model
- Go-to-Market: Marketing strategy, sales approach, launch planning

#### Entry Point 3: Path B - Start from Use Cases
- Discovery Mode Selection: User chooses [B] Use cases
- Use Case Intake: Gather N use cases (could be 3, 5, 10, 20+)
- Use Case Prioritization: Apply frameworks (separate for agentic vs application), select top 3
- Prototype Context Generation: Generate PROTOTYPE-{use-case}.md files for top 3
- Decision: Build prototypes now or hand off files to teams
- Prototype Building: Build from PROTOTYPE-*.md specifications (if user chooses to build)
- Selection: Pick winning use case from prototypes
- Product Strategy: For selected use case
- Go-to-Market: For selected use case

### Key Features:
- **PM-Focused**: Exclusively for Product Managers
- **Workshop-Friendly**: Teams can work in parallel with PROTOTYPE-*.md files
- **Scalable**: Supports any number of use cases (N)
- **Flexible**: Can stop after generating PROTOTYPE-*.md files for handoff
- **Transparent**: Always shows defaults, asks for LLM provider
- **Standard AIPLC**: Uses [Answer]: format throughout
- **Complete Output**: Discovery Document ready for developers

### What Happens After Discovery:
Developers receive the Discovery Document in a **separate workspace** and use it for:
- **Inception Phase**: Requirements Analysis, Workflow Planning, Application Design
- **Construction Phase**: Code Generation, Build & Test
- **Operations Phase**: Deployment, Monitoring

## Key Principles:
- **Discovery Only**: This workspace focuses exclusively on product definition
- **Three Entry Points**: Flexible starting points based on situation
- **PM-Led**: Product Managers drive the process
- **Developer Handoff**: Complete Discovery Document for seamless transition
- **Adaptive**: Workflow adjusts based on your needs and situation
