# Prototype Building

## Purpose
Build working prototypes from PROTOTYPE-{use-case}.md specifications.

## When to Execute
- Entry Point 1: PROTOTYPE-*.md files found in workspace (skip all discovery)
- After Prototype Context Generation (user chose to build now)
- User provides existing PROTOTYPE-*.md files

## Overview

This stage reads PROTOTYPE-{use-case}.md files and builds working prototypes that can be:
- Tested locally
- Iterated upon
- Validated by users
- Used for Product Strategy decisions

## Step 1: Identify PROTOTYPE-*.md Files

Scan for files matching pattern: `aiplc-docs/discovery/prototypes/*/PROTOTYPE-*.md`

List all found files:
```
I found {N} prototype specification file(s):

1. 📄 PROTOTYPE-{use-case-1-slug}.md
2. 📄 PROTOTYPE-{use-case-2-slug}.md
3. 📄 PROTOTYPE-{use-case-3-slug}.md

I'll build prototypes from these specifications.
```

## Step 2: For Each PROTOTYPE-*.md File

### Step 2.1: Read and Analyze Specification

Load the PROTOTYPE-*.md file and extract:
- Use case name and type (Agentic/Application)
- LLM provider and model (if specified)
- Tools/features
- Brand reference
- Device target
- Frontend requirements
- Any other specifications

### Step 2.2: Present Specification Summary

```
Building prototype {X} of {N}: {Use Case Name}

Here's what I found in the specification:

FROM SPECIFICATION:
✅ Use Case: {name}
✅ Type: {Agentic/Application}
✅ Tools: {tool1, tool2} (if specified)
✅ Brand Reference: {URL or description} (if specified)
✅ Target Device: {Mobile/Desktop/Both} (if specified)
✅ Frontend: {description} (if specified)

DEFAULTS FOR MISSING ITEMS:
🔧 LLM Provider: [Not specified - need your input] (if agentic and not specified)
🔧 LLM Model: Claude 3.5 Sonnet (default)
🔧 Port: {3000 + X} (default, incremented for each prototype)
🔧 Tools: {placeholder tools} (if not specified)
🔧 Brand: Generic modern design (if not specified)
🔧 Device: Both mobile and desktop (if not specified)

Would you like to:
[A] Proceed with these settings
[B] Update any of these settings

[Answer]:
```

### Step 2.3: Handle User Response

#### If [A] - Proceed:
- Continue to Step 2.4

#### If [B] - Update settings:

Ask:
```
Which settings would you like to update?

Current defaults:
1. LLM Model: {model}
2. Tools: {tools}
3. Brand: {brand}
4. Device: {device}
5. Port: {port}

Please specify what you'd like to change:
```

Gather updates, then show updated configuration and ask for confirmation again.

### Step 2.4: LLM Provider Selection (ALWAYS ASK for Agentic)

If use case is Agentic and LLM provider not specified:

```
Which LLM provider would you like to use for {Use Case Name}?

[A] AWS Bedrock (default - uses Claude Sonnet 4 via inference profile)
[B] Anthropic
[C] OpenAI
[D] Google Gemini
[E] Other

[Answer]:
```

Record selection.

**IMPORTANT: Set correct model based on provider:**
- **AWS Bedrock**: Use `us.anthropic.claude-sonnet-4-20250514-v1:0` (cross-region inference profile)
- **Anthropic**: Use `claude-sonnet-4-20250514`
- **OpenAI**: Use `gpt-5-mini` or `gpt-5.1`
- **Google Gemini**: Use `gemini-3-pro-preview` or `gemini-2.5-pro`

### Step 2.5: API Key Check and Request

**CREDENTIAL SECURITY RULE**:
- Only check whether credentials **exist** (non-empty) — never read, display, or echo their actual values
- Never log credential values in `audit.md` or any other file — log only "credentials configured: yes/no"
- If a user pastes a credential in chat, do NOT repeat it back — acknowledge receipt without displaying the value
- Never include credential values in AI-generated code, comments, or output files

Based on selected LLM provider, check for API credentials and ask upfront if missing:

**For Bedrock:**
- Check environment variables exist (non-empty): AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_DEFAULT_REGION
- Check AWS CLI configuration exists: ~/.aws/credentials

**For Anthropic:**
- Check environment variable exists (non-empty): ANTHROPIC_API_KEY

**For OpenAI:**
- Check environment variable exists (non-empty): OPENAI_API_KEY

**For Gemini:**
- Check environment variable exists (non-empty): GOOGLE_API_KEY

If credentials NOT found, present the following guidance:

```
## Setting Up Your API Credentials

Your API credentials must be set as **environment variables** in your terminal. This keeps them secure and out of any logged files.

⚠️  **IMPORTANT: Do NOT paste your credentials into this chat or any [Answer]: field.**
Set them in the terminal only. I will verify they are configured without seeing the actual values.

**What is an environment variable?** It's a setting in your computer's terminal that programs can read. You set it once per session, and any tool running in that terminal can use it.

### How to Set Environment Variables

**Step 1:** Open a terminal window:
- **VS Code / Cursor / Codex:** Use the built-in terminal (View → Terminal, or Ctrl+`)
- **Kiro:** Use the built-in terminal panel (Terminal → New Terminal)
- **Claude Code:** You're already in a terminal
- **Any other tool:** Open your operating system's terminal application (macOS: Terminal or iTerm; Windows: PowerShell)

**Step 2:** Copy and paste the commands below into your terminal, replacing the placeholder values with your actual credentials:
```

Then show the appropriate commands based on provider:

**For Bedrock:**
```
**macOS / Linux:**
  export AWS_DEFAULT_REGION=us-west-2
  export AWS_ACCESS_KEY_ID=paste-your-key-here
  export AWS_SECRET_ACCESS_KEY=paste-your-secret-here

**Windows (PowerShell):**
  $env:AWS_DEFAULT_REGION="us-west-2"
  $env:AWS_ACCESS_KEY_ID="paste-your-key-here"
  $env:AWS_SECRET_ACCESS_KEY="paste-your-secret-here"

Where to get these: AWS Console → IAM → Security Credentials → Access Keys
```

**For Anthropic:**
```
**macOS / Linux:**
  export ANTHROPIC_API_KEY=paste-your-key-here

**Windows (PowerShell):**
  $env:ANTHROPIC_API_KEY="paste-your-key-here"

Where to get this: https://console.anthropic.com/ → API Keys
```

**For OpenAI:**
```
**macOS / Linux:**
  export OPENAI_API_KEY=paste-your-key-here

**Windows (PowerShell):**
  $env:OPENAI_API_KEY="paste-your-key-here"

Where to get this: https://platform.openai.com/api-keys
```

**For Gemini:**
```
**macOS / Linux:**
  export GOOGLE_API_KEY=paste-your-key-here

**Windows (PowerShell):**
  $env:GOOGLE_API_KEY="paste-your-key-here"

Where to get this: https://aistudio.google.com/apikey
```

Then present confirmation question:

```
**Step 3:** Keep this terminal open — your AI tool must run in the same terminal session where you set the variables.

Once you've set your credentials in the terminal, confirm below:

[A] Done — I've set my credentials in the terminal
[B] I need help — show me the steps again
[C] I'm using AWS CLI profiles (already configured via `aws configure`)
[D] Use a different LLM provider

[Answer]:
```

**CRITICAL**: Do NOT offer options to paste credentials into [Answer]: fields. Credentials must only be set via the terminal. If a user accidentally pastes a credential in chat or an answer field, respond with: "I see you've shared a credential — please revoke it and generate a new one. Always set credentials in your terminal, never in chat." Do NOT log the credential.

After user confirms [A] or [C], verify credentials work by making a minimal API call:
```
✅ {Provider} credentials verified and working
```

If verification fails:
```
❌ {Provider} credentials verification failed

This usually means the credentials weren't set in the same terminal session, or the values are incorrect.

Options:
[A] I'll try setting them again in my terminal (show me the steps)
[B] Use a different LLM provider

[Answer]:
```

### Step 2.6: Final Configuration Confirmation

```
Ready to build the {Use Case Name} prototype with:

Configuration:
- Type: {Agentic/Application}
- LLM Provider: {provider} (if agentic)
- LLM Model: {model} (if agentic)
- Tools: {tool1, tool2}
- Brand: {URL or description}
- Device: {Mobile/Desktop/Both}
- Port: {port}
- Deployment: http://localhost:{port}

This will:
1. Activate Strands Power (if agentic)
2. Build the {agent/application} with specified {tools/features}
3. Create the frontend matching {brand}
4. Deploy locally for testing

Proceed with building the prototype?

[A] Yes, build the prototype
[B] No, I need to make changes

[Answer]:
```

### Step 2.7: Build Prototype

If [A] - Yes:

#### Environment Detection for Agentic Use Cases

Before building, detect the environment and configure Strands accordingly:

**Detection Logic:**
1. Check if `.kiro/` directory exists → **Kiro environment**
2. Otherwise → **All other environments** (Claude Code, Copilot, Cursor, Cline, etc.)

**Path 1 — Kiro:**
- Activate Strands Power (built-in Kiro Power integration)
- No additional setup needed
- Proceed with building

**PROTOTYPE ENVIRONMENT RULES** (applies to Path 2 only — Kiro Power handles isolation internally):
- Always create a virtual environment (`python -m venv .venv`) before installing any packages — never install to the system Python
- Pin package versions when installing (e.g., `pip install strands-agents==0.1.x flask==3.x.x`) — use latest stable versions available
- Only install packages from PyPI (the official Python package index) — never install from arbitrary URLs or git repos
- Prototypes run locally only (localhost) — do not expose ports to the network or deploy to remote servers
- Do not install packages or run code that requires root/sudo permissions

**Path 2 — All other environments:**
- Present the following question:

```
## Question
We need the Strands SDK to build your AI agent. How brave are you feeling today?

A) Mock it — fake the agent responses so I can see the UI and flow without installing anything. I'll let the developers handle the real wiring later. (No SDKs, no drama, just vibes.)
B) Let's ride — I trust you, AI. Install whatever you need and let's build this thing for real. Hold my coffee. ☕

[Answer]:
```

- If [A] Mock: Build frontend with hardcoded mock responses simulating the agent. Skip Strands installation entirely. Mark prototype as "UI Prototype — Agent Mocked" in iteration log.
- If [B] Ride: Create a virtual environment first (`python -m venv .venv && source .venv/bin/activate`), then install with pinned versions: `pip install strands-agents strands-agents-tools flask flask-cors`. Do NOT install to system Python. Proceed with full build.

---

Show progress:
```
Building {Use Case Name} prototype...

Step 1/{total}: Setting up Strands agent... (if agentic)
```

**For Agentic Use Cases:**
1. Set up Strands agent (via Power, MCP, install, or mock — based on environment)
2. Configure LLM provider and model
3. Implement specified tools
4. Create agent orchestration logic
5. Build frontend interface
6. Set up local deployment
7. Test basic functionality

**For Application Use Cases:**
1. Set up project structure
2. Implement specified features
3. Create UI components
4. Apply brand styling
5. Set up local deployment
6. Test basic functionality

Show progress for each step:
```
Step 2/{total}: Building agent with {provider} {model}...
Step 3/{total}: Implementing tools: {tool1}, {tool2}...
Step 4/{total}: Creating {device} frontend...
Step 5/{total}: Applying {brand} styling...
Step 6/{total}: Deploying to http://localhost:{port}...
Step 7/{total}: Running basic tests...
```

**SECURITY NOTE**: Prototypes are for local demonstration only. They run on localhost and must not be exposed to external networks or deployed to production/public-facing environments from this workshop.

### Step 2.8: Present Completion

```
✅ {Use Case Name} prototype is ready!

Running at: http://localhost:{port}

The prototype includes:
- {Key feature 1}
- {Key feature 2}
- {Key feature 3}
- {Brand} styling
- {Device} optimized interface

Please test the prototype and let me know if you'd like any iterations.

What would you like to do?
[A] Test and iterate on this prototype
[B] Continue to next prototype (if more exist)
[C] This prototype is good, move on

[Answer]:
```

### Step 2.9: Handle Iteration (if requested)

If [A] - Test and iterate:

```
What changes would you like to make to the prototype?

You can request:
- UI/design changes
- Functionality adjustments
- Tool modifications
- Performance improvements
- Bug fixes

Describe the changes:
```

Make requested changes, redeploy, and ask for validation again.

Log iterations in: `aiplc-docs/discovery/prototypes/{use-case-slug}/iteration-log.md`

```markdown
## Iteration {N}
**Timestamp**: {timestamp}
**Requested Changes**: {user request}
**Changes Made**: {what was changed}
**Result**: {outcome}
```

Repeat until user is satisfied.

## Step 3: After All Prototypes Built

If multiple prototypes were built:

```
✅ All {N} prototypes are complete!

Summary:
1. {Use Case 1} - http://localhost:{port1} - {Status}
2. {Use Case 2} - http://localhost:{port2} - {Status}
3. {Use Case 3} - http://localhost:{port3} - {Status}

Which prototype would you like to move forward with for 
Product Strategy and Go-to-Market?

[A] {Use Case 1}
[B] {Use Case 2}
[C] {Use Case 3}
[D] Multiple use cases
[E] None - need more iteration

[Answer]:
```

If single prototype:

```
✅ {Use Case Name} prototype is complete!

Ready to move to Product Strategy for this use case?

[A] Yes, continue to Product Strategy
[B] No, I need more iterations

[Answer]:
```

## Step 4: Selection and Next Steps

Record selected use case(s) and proceed to Product Strategy stage.

## Audit Logging

```markdown
## Prototype Building - {Use Case Name}
**Timestamp**: [ISO timestamp]
**User Input**: "[All user responses during building]"
**AI Response**: "Built prototype for {Use Case Name}. Deployed at http://localhost:{port}."
**Context**: Prototype building complete

---

## Prototype Building - Configuration
**Timestamp**: [ISO timestamp]
**Use Case**: {Name}
**Configuration**: {Full configuration details}
**User Input**: "[User's configuration confirmations]"
**Context**: Configuration confirmed

---

## Prototype Building - Iteration {N}
**Timestamp**: [ISO timestamp]
**Use Case**: {Name}
**User Input**: "[Requested changes]"
**AI Response**: "Made changes: {summary}. Redeployed."
**Context**: Prototype iteration

---

## Prototype Building - Selection
**Timestamp**: [ISO timestamp]
**User Input**: "[Selected use case]"
**AI Response**: "User selected {Use Case Name} to move forward. Proceeding to Product Strategy."
**Context**: Prototype selection complete
```

## Next Steps

Proceed to: Product Strategy stage for selected use case(s)
