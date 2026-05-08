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

Based on selected LLM provider, check for API credentials and ask upfront if missing:

**For Bedrock:**
- Check environment variables: AWS_BEARER_TOKEN_BEDROCK, AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_REGION
- Check AWS CLI configuration: ~/.aws/credentials

If credentials NOT found:
```
⚠️  AWS Bedrock credentials not found

To use AWS Bedrock, you need either:

Option 1 (Development - Recommended):
  export AWS_BEARER_TOKEN_BEDROCK=your_bearer_token

Option 2 (Production):
  export AWS_ACCESS_KEY_ID=your_access_key
  export AWS_SECRET_ACCESS_KEY=your_secret_key
  export AWS_REGION=us-west-2

Please provide your credentials:
[A] I have AWS credentials configured (will check again)
[B] I'll provide AWS_BEARER_TOKEN_BEDROCK now
[C] I'll provide AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY now
[D] Use a different LLM provider

[Answer]:
```

If [B], ask:
```
Please provide your AWS_BEARER_TOKEN_BEDROCK:
(Format: export AWS_BEARER_TOKEN_BEDROCK=bedrock-api-key-...)

[Answer]:
```

If [C], ask:
```
Please provide your AWS credentials:

AWS_ACCESS_KEY_ID: [Answer]:
AWS_SECRET_ACCESS_KEY: [Answer]:
AWS_REGION (default us-west-2): [Answer]:
```

**For Anthropic:**
- Check environment variable: ANTHROPIC_API_KEY

If NOT found:
```
⚠️  Anthropic API key not found

Please provide your ANTHROPIC_API_KEY:
(Get it from: https://console.anthropic.com/)

[Answer]:
```

**For OpenAI:**
- Check environment variable: OPENAI_API_KEY

If NOT found:
```
⚠️  OpenAI API key not found

Please provide your OPENAI_API_KEY:
(Get it from: https://platform.openai.com/api-keys)

[Answer]:
```

**For Gemini:**
- Check environment variable: GOOGLE_API_KEY

If NOT found:
```
⚠️  Google API key not found

Please provide your GOOGLE_API_KEY:
(Get it from: https://aistudio.google.com/apikey)

[Answer]:
```

After receiving credentials, verify they work before proceeding:
```
✅ {Provider} credentials verified and working
```

If verification fails:
```
❌ {Provider} credentials verification failed

Error: {error message}

Options:
[A] Try different credentials
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

Show progress:
```
Building {Use Case Name} prototype...

Step 1/{total}: Activating Strands Power... (if agentic)
```

**For Agentic Use Cases:**
1. Activate Strands Power (use Kiro Power integration)
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
