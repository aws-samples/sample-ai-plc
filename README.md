# AI-PLC Discovery Workspace

A Product Manager-focused workspace for defining and validating AI product ideas using the AI Product Lifecycle (AI-PLC) Discovery Phase.

## What is This?

This workspace helps Product Managers complete the Discovery phase of AI-PLC - the critical first step where you define **WHO** your customer is, **WHAT** problem you're solving, and **WHY** it matters, before any technical development begins.

## Who Should Use This?

- **Product Managers** leading AI product initiatives
- **Product Teams** evaluating multiple use cases
- **Workshop Facilitators** running AI product discovery sessions
- **Innovation Teams** exploring AI opportunities

## What You'll Get

### Main Output
A comprehensive **Discovery Document** containing:
- Customer pain points and insights
- PR/FAQ using Amazon's Working Backwards method
- Use case analysis and prioritization
- PROTOTYPE-*.md specifications (portable, shareable)
- Product strategy and positioning
- Go-to-market plan

### Ready for Handoff
Everything developers need to start building in their own workspace:
- Clear product vision and requirements
- Validated use cases
- Prototype specifications
- Strategic context

## Three Ways to Start

### Entry Point 1: Existing Prototype Specs
**You have**: PROTOTYPE-*.md files from a workshop or previous session  
**What happens**: Build prototypes immediately, skip discovery phases  
**Best for**: Workshop teams with pre-generated specifications

**Example Prompts:**
- "I want to build prototypes from existing PROTOTYPE files"
- "Start the AI-PLC workflow to build my prototypes"
- "I have PROTOTYPE-*.md files ready, let's build them"

### Entry Point 2: Customer Pain Points
**You have**: Customer feedback, reviews, or pain points  
**What happens**: Create PR/FAQ → Analyze solutions → Build prototypes  
**Best for**: Starting from customer insights

**Example Prompts:**
- "I want to start AI-PLC Discovery from customer pain points"
- "Help me create a PR/FAQ from customer feedback"
- "I have customer reviews and want to identify AI solutions"
- "Start Discovery workflow from pain points"

### Entry Point 3: Multiple Use Cases
**You have**: 3, 5, 10, or 20+ use case ideas to evaluate  
**What happens**: Prioritize → Select top 3 → Generate specs → Build prototypes  
**Best for**: Teams with many ideas needing prioritization

**Example Prompts:**
- "I have 10 use cases that need prioritization using AI-PLC"
- "Start AI-PLC Discovery workflow for use case prioritization"
- "Help me prioritize multiple AI agent ideas"
- "I want to evaluate and rank my use cases"

## Workflow Overview

```
Product Manager Request
         ↓
Workspace Detection
         ↓
Check for PROTOTYPE-*.md files?
         ↓
    ┌────┴────┐
    ↓         ↓
Entry Point 1  Entry Points 2 & 3
Existing Files Pain Points or Use Cases
    ↓              ↓
    └──────┬───────┘
           ↓
   Prototype Building (Optional)
           ↓
   Product Strategy
           ↓
   Go-to-Market
           ↓
   Discovery Document Complete
```

## Quick Start

### Prerequisites

**Required Software:**

#### 1. Kiro IDE Installation
- Download and install from [https://kiro.dev/docs/getting-started/installation/#download-kiro](https://kiro.dev/docs/getting-started/installation/#download-kiro)
- Follow the installation guide for your operating system (Windows, macOS, or Linux)

#### 2. Git Installation
Git is required to download the AI-PLC workspace from GitHub.

**Step 1: Check if Git is already installed**
1. Open Terminal (macOS/Linux) or Command Prompt (Windows)
2. Type: `git --version` and press Enter
3. If you see a version number (like "git version 2.39.0"), Git is already installed - skip to step 3!

**Step 2: Install Git (if not already installed)**

**For Windows:**
1. Open Command Prompt as Administrator (right-click → "Run as administrator")
2. Type: `winget install Git.Git` and press Enter
3. Wait for installation to complete
4. Close and reopen Command Prompt
5. Verify: `git --version`

**For macOS:**
1. Open Terminal
2. Type: `git --version` and press Enter
3. If Git is not installed, macOS will automatically prompt you to install it
4. Click "Install" and follow the prompts
5. Verify: `git --version`

**For Linux (Ubuntu/Debian):**
1. Open Terminal
2. Type: `sudo apt update && sudo apt install git` and press Enter
3. Enter your password when prompted
4. Verify: `git --version`

**Step 3: Verify Git is working**
Type this command to test Git is properly installed:
```bash
git --help
```
You should see Git help information displayed.

**System Requirements:**
- **Admin/Installation Permissions**: You need permissions to install packages (Python, Node.js, etc.) that will be automatically installed during the prototype building process in Kiro
- **Internet Connection**: Required for package downloads and API access

**For AI Agent Applications:**
- **LLM API Keys**: Required for accessing Large Language Models (e.g., AWS Bedrock, OpenAI, Anthropic)
- **Strands SDK**: Used for building AI agents - will be automatically installed during prototype building

**Knowledge Requirements:**
- Basic understanding of your product domain
- Customer insights or use case ideas (optional)

### Getting Started

1. **Clone the AI-PLC branch** (not main branch)
   ```bash
   git clone -b ai-plc-prioritize-prototype-agents https://github.com/RachnaC1234/aidlc-workflows.git
   cd aidlc-workflows
   ```
   
   **Note**: The `git clone` command creates a new folder called `aidlc-workflows` containing all the workspace files.

2. **Open in Kiro IDE**
   ```bash
   kiro .
   ```
   Or open Kiro IDE and use File → Open Workspace to select the cloned folder.

3. **Enable Vibe Mode**
   - Once Kiro IDE opens, activate **Vibe Mode** for the AI-PLC workflow
   - This enables the AI assistant to guide you through the discovery process

4. **Start the workflow**
   - The AI will automatically detect your workspace
   - Check for existing PROTOTYPE-*.md files
   - Guide you through the appropriate entry point
   
   **Choose ONE prompt based on what you have:**
   
   **Entry Point 1 - If you have PROTOTYPE-*.md files (pick one):**
   - `"I want to build prototypes from existing PROTOTYPE files"`
   - `"Start the AI-PLC workflow to build my prototypes"`
   - `"I have PROTOTYPE-*.md files ready, let's build them"`
   
   **Entry Point 2 - If you have customer pain points (pick one):**
   - `"I want to start AI-PLC Discovery from customer pain points"`
   - `"Help me create a PR/FAQ from customer feedback"`
   - `"I have customer reviews and want to identify AI solutions"`
   - `"Start Discovery workflow from pain points"`
   
   **Entry Point 3 - If you have multiple use cases to prioritize (pick one):**
   - `"I have 10 use cases that need prioritization using AI-PLC"`
   - `"Start AI-PLC Discovery workflow for use case prioritization"`
   - `"Help me prioritize multiple AI agent ideas"`
   - `"I want to evaluate and rank my use cases"`

5. **Follow the guided process**
   - Answer questions using [Answer]: format
   - Review and approve each stage
   - Make product decisions on strategy and positioning
   
   **Important**: Sometimes Kiro may start asking questions directly in the chat interface instead of creating question files for you to fill out. If this happens, remind Kiro by saying:
   
   ```
   "Please create a question file (.md) with [Answer]: tags instead of asking in chat, so my answers can be logged and audited later"
   ```
   
   This ensures all your responses are properly documented in the audit trail for future reference.

**Note**: Additional software packages (Python libraries, Node.js packages) may be installed automatically during the prototype building process.

## Workflow Overview

```
Product Manager Request
         ↓
Workspace Detection
         ↓
Check for PROTOTYPE-*.md files?
         ↓
    ┌────┴────┐
    ↓         ↓
Entry Point 1  Entry Points 2 & 3
Existing Files Pain Points or Use Cases
    ↓              ↓
    └──────┬───────┘
           ↓
   Prototype Building (Optional)
           ↓
   Product Strategy
           ↓
   Go-to-Market
           ↓
   Discovery Document Complete
```

## Key Features

- **PM-Focused**: No coding required - focuses on product vision
- **Three Entry Points**: Flexible starting points based on your situation
- **Scalable**: Supports any number of use cases (3, 5, 10, 20+)
- **Workshop-Friendly**: PROTOTYPE-*.md files are portable and shareable
- **Transparent**: Always shows defaults, asks for your input
- **Documented**: Complete audit trail of all decisions
- **Handoff-Ready**: Produces comprehensive Discovery Document for developers

## What Happens After Discovery?

Developers receive your Discovery Document in a **separate workspace** where they:
1. **Inception Phase**: Requirements analysis, workflow planning, application design
2. **Construction Phase**: Code generation, build, and test
3. **Operations Phase**: Deployment and monitoring

## Example Use Cases

### Workshop Scenario
- Facilitator generates 5 PROTOTYPE-*.md files
- Distributes to 5 teams
- Each team opens workspace, builds their prototype
- Teams present and compare results

### Startup Scenario
- PM has 10 potential AI agent ideas
- Uses Entry Point 3 to prioritize
- Selects top 3 for prototyping
- Generates PROTOTYPE-*.md files
- Hands off to engineering team

### Customer-Driven Scenario
- PM collects customer reviews from Trustpilot
- Uses Entry Point 2 with URL
- Creates PR/FAQ
- Builds and validates prototype
- Defines strategy and GTM

## Directory Structure

```
ai-plc-discovery-workspace/
├── README.md                          # This file
├── .kiro/
│   ├── aws-aiplc-rule-details/       # Workflow rules
│   │   ├── common/                   # Common guidelines
│   │   ├── discovery/                # Discovery phase rules
│   │   └── inception/                # Workspace detection only
│   └── steering/
│       └── aws-aiplc-rules/          # Core workflow
└── aiplc-docs/                       # Generated during workflow
    ├── discovery/
    │   ├── discovery-document.md     # Main output ★
    │   ├── envision/                 # Pain points & PR/FAQ
    │   ├── use-case-intake/          # Use case details
    │   ├── prioritization/           # Scoring & ranking
    │   ├── prototypes/               # PROTOTYPE-*.md files ★
    │   ├── product-strategy/         # Strategy docs
    │   └── go-to-market/             # GTM plans
    ├── aiplc-state.md               # Session state
    └── audit.md                      # Complete audit trail
```

## Support

For questions, issues, or contributions:
- Open an issue in this repository
- Refer to the documentation in `.kiro/aws-aiplc-rule-details/`
- Check the welcome message for detailed workflow guidance

## License

[Add your license here]

## Contributing

[Add contribution guidelines here]

## Security Considerations

This workflow is designed for **local prototyping only** — not production use.
Be aware of the following:

- **Prototypes have no authentication.** Generated apps run on localhost
  with no auth layer. Never expose them on a public network.

- **PROTOTYPE-*.md files are trusted as specifications.** Only use files
  you or your team created. Do not import PROTOTYPE-*.md files from
  untrusted sources — they drive code generation directly.

- **Audit logs capture your full input.** `audit.md` and `aiplc-state.md`
  contain verbatim session data. Do not commit these to shared repositories
  if you've entered sensitive business information.

- **Credentials are environment-variable based.** Never paste API keys
  into chat. If you accidentally do, revoke and regenerate them. The
  workflow will attempt to redact recognized patterns but cannot catch all
  credential formats.

- **URL fetching has basic SSRF protections** but is not hardened against
  advanced bypass techniques (DNS rebinding, IPv6, redirects). Only provide
  URLs you trust.

- **Session state (`aiplc-state.md`) is not integrity-checked.** In shared
  workshop environments, be aware that manual edits to this file can skip
  workflow gates.

- **For AWS credentials:** prefer temporary credentials (SSO/assumed roles)
  over long-lived access keys. If using temporary credentials, also set
  `AWS_SESSION_TOKEN`.

---

**Ready to start?** Open this workspace in Kiro IDE and let the AI guide you through your Discovery journey!
