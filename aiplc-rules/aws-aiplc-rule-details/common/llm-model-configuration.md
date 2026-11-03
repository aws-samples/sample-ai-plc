# LLM Model Configuration Guide

## Purpose
Single source of truth for choosing the LLM model, region, and request parameters for agentic prototypes. Other rule files refer to this file instead of naming model IDs themselves.

## Principles

1. **Never hardcode a model ID from memory.** Model versions are retired over time and model IDs differ by region. Resolve the model ID at build time (see below), confirm it with the user, and record it in the prototype's `iteration-log.md`.
2. **Default model family**: For AWS Bedrock and Anthropic, the default is the **newest active Claude Sonnet model**. The user can choose another model.
3. **Do not set sampling parameters for Claude models.** Do not pass `temperature`, `top_p`, or `top_k` — current Claude models reject non-default values with a validation error. For other providers, leave sampling at the provider default unless the user asks.
4. **Default `max_tokens`**: `16000`. Lower values can truncate responses, because current models count reasoning tokens against the limit.

## AWS Bedrock

### Resolve the Model ID at Build Time

Bedrock on-demand calls to Claude models use an **inference profile ID**, not the bare model ID. Profiles have a prefix that depends on the region: a geographic prefix (for example `us.`, `eu.`, `apac.`) or `global.`. A profile that exists in one region may not exist in another — for example, `us.` profiles are not available in `ap-northeast-2` (Seoul).

1. **Region**: Use the region the user chose (ask if not set). Do not assume `us-west-2`.
2. **If the AWS CLI is available and credentials are configured**, list what the region actually offers:

```bash
# Active Anthropic models in the region
aws bedrock list-foundation-models --region <region> --by-provider Anthropic \
  --query "modelSummaries[?modelLifecycle.status=='ACTIVE'].modelId" --output text

# Inference profiles available in the region
aws bedrock list-inference-profiles --region <region> --type-equals SYSTEM_DEFINED \
  --query "inferenceProfileSummaries[?contains(inferenceProfileId, 'anthropic.claude-sonnet')].inferenceProfileId" --output text
```

   - Pick the highest-versioned **ACTIVE** Sonnet model (for example `sonnet-5-5` is newer than `sonnet-5`, which is newer than `sonnet-4-6`). Never pick a model whose lifecycle status is `LEGACY`.
   - Use the inference profile for that model with the region's geographic prefix if one is listed; otherwise use the `global.` profile and tell the user that global profiles can route requests to other geographies.
3. **If the CLI is not available** (some IDEs, sandboxes, or hosts without AWS tooling): ask the user for the inference profile ID in a question file. Tell them where to find it: Amazon Bedrock console → the region they use → Cross-region inference (inference profiles). Show the examples below for the expected format.
4. Present the resolved ID with the other defaults and let the user confirm or change it.

### Example IDs (Last verified: 2026-10-26)

Examples only — always resolve the current ID with the steps above.

| Region | Example inference profile ID |
|---|---|
| `us-west-2` | `us.anthropic.claude-sonnet-5-5` or `global.anthropic.claude-sonnet-5-5` |
| `ap-northeast-2` | `global.anthropic.claude-sonnet-5-5` (no `us.` profiles in this region) |

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
export AWS_REGION=<region>
```
- Best for production deployments
- Use IAM roles or temporary credentials
- Configure via `aws configure` or environment variables

### Python Code Example (Strands SDK)
```python
from strands.models import BedrockModel

model = BedrockModel(
    model_id="<inference-profile-id resolved above>",
    region_name="<region>",
    max_tokens=16000,
)
```

### Common Errors and Solutions

**Error: "This model version has reached the end of its life"** (or the model is listed as `LEGACY`)
- Cause: The model ID was hardcoded or copied from an older example
- Solution: Resolve the model ID again with the steps above and pick an ACTIVE model

**Error: "Invocation of model ID ... with on-demand throughput isn't supported"**
- Cause: Using the bare model ID instead of an inference profile ID
- Solution: Use the inference profile ID listed for your region (geographic prefix or `global.`)

**Error: "The provided model identifier is invalid"** for an ID with a prefix
- Cause: The profile prefix does not exist in this region (for example `us.` in `ap-northeast-2`)
- Solution: List the region's inference profiles and use one that exists there

**Error: "ValidationException" mentioning `temperature`, `top_p`, or `top_k`**
- Cause: Sampling parameters sent to a Claude model that accepts only the defaults
- Solution: Remove those parameters

**Error: "ResourceNotFoundException" or "Access denied"**
- Cause: Model access not granted for this account and region, or the IAM policy does not allow invoking the model
- Solution: Check model access in the Amazon Bedrock console for the region, and the IAM permissions for `bedrock:InvokeModel*`

## Anthropic Direct

### Model ID
Use the newest Claude Sonnet model listed at https://platform.claude.com/docs/en/about-claude/models/overview (example, last verified 2026-10-26: `claude-sonnet-5-5`). Confirm with the user.

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
    model_id="<model-id confirmed with the user>",
    max_tokens=16000,
)
```

## Other Providers (OpenAI, Google Gemini, Meta Llama, Others)

Model names for these providers change frequently and are not tracked in this file. Ask the user which model to use, and point them to the provider's current model list:

| Provider | Model list | Environment Variable | Get Key From |
|----------|-----------|---------------------|--------------|
| OpenAI | https://platform.openai.com/docs/models | `OPENAI_API_KEY` | platform.openai.com/api-keys |
| Google Gemini | https://ai.google.dev/gemini-api/docs/models | `GOOGLE_API_KEY` | aistudio.google.com/apikey |
| Meta Llama | https://llama.developer.meta.com/docs/models | `LLAMA_API_KEY` | llama.developer.meta.com |

### Python Code Examples (Strands SDK)
```python
import os

# OpenAI
from strands.models.openai import OpenAIModel
model = OpenAIModel(
    client_args={"api_key": os.environ["OPENAI_API_KEY"]},
    model_id="<model-id confirmed with the user>",
)

# Google Gemini
from strands.models.gemini import GeminiModel
model = GeminiModel(
    client_args={"api_key": os.environ["GOOGLE_API_KEY"]},
    model_id="<model-id confirmed with the user>",
)

# Meta Llama
from strands.models.llamaapi import LlamaAPIModel
model = LlamaAPIModel(
    client_args={"api_key": os.environ["LLAMA_API_KEY"]},
    model_id="<model-id confirmed with the user>",
)
```

## Quick Reference Table

| Provider | Model ID | Environment Variable | Get Key From |
|----------|----------|---------------------|--------------|
| AWS Bedrock | Resolved per region at build time (see above) | `AWS_BEARER_TOKEN_BEDROCK` or `AWS_ACCESS_KEY_ID` + `AWS_SECRET_ACCESS_KEY` | AWS Bedrock Console |
| Anthropic | Newest Claude Sonnet, confirmed with the user | `ANTHROPIC_API_KEY` | console.anthropic.com |
| OpenAI / Gemini / Llama | Asked from the user | See table above | See table above |

## Workflow Integration

When building prototypes in the Discovery phase:

1. **Always ask for LLM provider** (even if default is Bedrock)
2. **Resolve the model ID** for the provider (and region, for Bedrock) using this file — never from memory
3. **Check for API credentials** before building
4. **Request credentials upfront** if missing (don't wait until build fails)
5. **Verify credentials and the model ID work** with a minimal call before proceeding with the prototype build
6. **Record** the provider, region, and model ID in the prototype's `iteration-log.md`

This ensures smooth prototype building without credential or model errors mid-process.
