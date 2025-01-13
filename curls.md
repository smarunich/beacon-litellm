# LiteLLM API Curl Examples

## Health Check
```bash
# Check if the service is ready
curl http://localhost:4000/health/readiness

# Check if the service is alive
curl http://localhost:4000/health/liveliness
```

## Chat Completion with Claude
```bash
# Basic chat completion with bedrock-claude-v1
curl http://localhost:4000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer sk-1234" \
  -d '{
    "model": "bedrock-claude-v1",
    "messages": [
      {
        "role": "user",
        "content": "Hello! How can you help me today?"
      }
    ]
  }'
```

## Models List
```bash
# Get available models
curl http://localhost:4000/v1/models \
  -H "Authorization: Bearer sk-1234"
```

## Bedrock Pass-through Example
```bash
# Direct Bedrock API call through proxy
curl http://localhost:4000/bedrock/model/anthropic.claude-instant-v1/invoke \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer sk-1234" \
  -d '{
    "prompt": "\n\nHuman: Hello! How can you help me today?\n\nAssistant:",
    "max_tokens_to_sample": 500,
    "temperature": 0.7,
    "top_p": 1
  }'


curl --location "http://localhost:4000/chat/completions" \
  --header 'Content-Type: application/json' \
  --header 'Authorization: Bearer sk-1234' \
  --data '{
    "model": "bedrock-claude-v1",
    "messages": [
      {
        "role": "user",
        "content": "what is Amazon S3"
      }
    ]
  }'
