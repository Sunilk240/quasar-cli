# Groq

Groq provides fast inference with competitive pricing.

---

## Get API Key

1. Go to [console.groq.com](https://console.groq.com)
2. Sign up or log in
3. Navigate to API Keys
4. Create a new API key

---

## Configuration

Add to your `.env` file:

```env
GROQ_API_KEY_1=gsk_your_key_here
GROQ_API_KEY_2=gsk_your_second_key_here
```

---

## Available Models

| Model | Description | Tool Calling |
|-------|-------------|--------------|
| `openai/gpt-oss-120b` | Large, versatile | ✅ Excellent |
| `openai/gpt-oss-20b` | Smaller, faster | ✅ Good |
| `llama-3.3-70b-versatile` | Meta's Llama | ⚠️ Limited |
| `meta-llama/llama-4-scout-17b-16e-instruct` | Latest Llama | ⚠️ Limited |

!!! tip "Recommended"
    Use `openai/gpt-oss-120b` for best tool calling support.

---

## Usage

```bash
# Auto mode (Groq used as fallback)
quasar "your request"

# Force Groq
quasar --model groq/openai/gpt-oss-120b "your request"
```

---

## Rate Limits

Groq has rate limits on free tier:

- Requests per minute
- Tokens per day

**Tip:** Add multiple API keys for automatic rotation:

```env
GROQ_API_KEY_1=gsk_first_key
GROQ_API_KEY_2=gsk_second_key
GROQ_API_KEY_3=gsk_third_key
```

---

## Troubleshooting

### Rate Limit Error

```
Error: 429 Too Many Requests
```

**Solutions:**

1. Wait a few seconds and retry
2. Add more API keys
3. Use a different provider

### Tool Calling Issues

Some Groq models have tool calling problems. Use `openai/gpt-oss-120b` for best results.
