# LLM Model Configuration Guide

## Purpose
Reference guide for correct LLM model IDs and API credential configuration across different providers.

## AWS Bedrock Configuration

### Correct Model ID
**ALWAYS use the cross-region inference profile for Claude Sonnet 4:**
```
us.anthropic.claude-sonnet-4-20250514-v1:0
```

**DO NOT use the direct model ID** (will fail with on-demand throughput error):
```
❌ anthropic.claude-sonnet-4-20250514-v1:0  (WRONG - causes ValidationException)
```

### API Credentials

**Option 1: Bearer Token (Development - Recommended)**
```bash
export AWS_BEARER_TOKEN_BEDROCK=bedrock-api-key-...
```
- Best for development and testing
- Expires in 30 days
- Get from: AWS Bedrock Console → API keys

**Option 2: AWS Credentials (Production)**
```bash
export AWS_ACCESS_KEY_ID=your_access_key
export AWS_SECRET_ACCESS_KEY=your_secret_key
export AWS_REGION=us-west-2
```
- Best for production deployments
- Use IAM roles or temporary credentials
- Configure via `aws configure` or environment variables

### Python Code Example (Strands SDK)
```python
from strands.models import BedrockModel
import os

# Check for bearer token
bearer_token = os.environ.get("AWS_BEARER_TOKEN_BEDROCK")

# Use cross-region inference profile
model = BedrockModel(
    model_id="us.anthropic.claude-sonnet-4-20250514-v1:0",
    region_name="us-west-2",
    temperature=0.7,
    max_tokens=2048,
)
```

### Common Errors and Solutions

**Error: "This model version has reached the end of its life"**
- Cause: Using deprecated model version (e.g., claude-3-5-sonnet-20241022-v2:0)
- Solution: Use Claude Sonnet 4: `us.anthropic.claude-sonnet-4-20250514-v1:0`

**Error: "Invocation of model ID ... with on-demand throughput isn't supported"**
- Cause: Using direct model ID instead of inference profile
- Solution: Add `us.` prefix: `us.anthropic.claude-sonnet-4-20250514-v1:0`

**Error: "ResourceNotFoundException" or "Access denied"**
- Cause: Model access not enabled in Bedrock console
- Solution: 
  1. Open AWS Bedrock Console
  2. Navigate to "Model access"
  3. Enable "Claude Sonnet 4"
  4. Wait a few minutes for access to propagate

## Anthropic Direct Configuration

### Model ID
```
claude-sonnet-4-20250514
```

### API Credentials
```bash
export ANTHROPIC_API_KEY=your_anthropic_api_key
```
- Get from: https://console.anthropic.com/

### Python Code Example
```python
from strands.models.anthropic import AnthropicModel
import os

model = AnthropicModel(
    client_args={"api_key": os.environ["ANTHROPIC_API_KEY"]},
    model_id="claude-sonnet-4-20250514",
    max_tokens=2048,
    params={"temperature": 0.7}
)
```

## OpenAI Configuration

### Model IDs
```
gpt-5-mini
gpt-5.1
```

### API Credentials
```bash
export OPENAI_API_KEY=your_openai_api_key
```
- Get from: https://platform.openai.com/api-keys

### Python Code Example
```python
from strands.models.openai import OpenAIModel
import os

model = OpenAIModel(
    client_args={"api_key": os.environ["OPENAI_API_KEY"]},
    model_id="gpt-5-mini",
)
```

## Google Gemini Configuration

### Model IDs
```
gemini-3-pro-preview
gemini-2.5-pro
gemini-2.5-flash
```

### API Credentials
```bash
export GOOGLE_API_KEY=your_google_api_key
```
- Get from: https://aistudio.google.com/apikey

### Python Code Example
```python
from strands.models.gemini import GeminiModel
import os

model = GeminiModel(
    client_args={"api_key": os.environ["GOOGLE_API_KEY"]},
    model_id="gemini-3-pro-preview",
)
```

## Meta Llama Configuration

### Model IDs
```
Llama-4-Maverick-17B-128E-Instruct-FP8
Llama-3.3-70B-Instruct
Llama-3.2-90B-Vision-Instruct
```

### API Credentials
```bash
export LLAMA_API_KEY=your_llama_api_key
```
- Get from: https://llama.developer.meta.com/

### Python Code Example
```python
from strands.models.llamaapi import LlamaAPIModel
import os

model = LlamaAPIModel(
    client_args={"api_key": os.environ["LLAMA_API_KEY"]},
    model_id="Llama-4-Maverick-17B-128E-Instruct-FP8",
    temperature=0.7,
    max_completion_tokens=2048
)
```

## Quick Reference Table

| Provider | Model ID | Environment Variable | Get Key From |
|----------|----------|---------------------|--------------|
| AWS Bedrock | `us.anthropic.claude-sonnet-4-20250514-v1:0` | `AWS_BEARER_TOKEN_BEDROCK` or `AWS_ACCESS_KEY_ID` + `AWS_SECRET_ACCESS_KEY` | AWS Bedrock Console |
| Anthropic | `claude-sonnet-4-20250514` | `ANTHROPIC_API_KEY` | console.anthropic.com |
| OpenAI | `gpt-5-mini` or `gpt-5.1` | `OPENAI_API_KEY` | platform.openai.com/api-keys |
| Google Gemini | `gemini-3-pro-preview` | `GOOGLE_API_KEY` | aistudio.google.com/apikey |
| Meta Llama | `Llama-4-Maverick-17B-128E-Instruct-FP8` | `LLAMA_API_KEY` | llama.developer.meta.com |

## Workflow Integration

When building prototypes in the Discovery phase:

1. **Always ask for LLM provider** (even if default is Bedrock)
2. **Set correct model ID** based on provider selection
3. **Check for API credentials** before building
4. **Request credentials upfront** if missing (don't wait until build fails)
5. **Verify credentials work** before proceeding with prototype build

This ensures smooth prototype building without credential errors mid-process.
