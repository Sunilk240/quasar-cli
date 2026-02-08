# Cerebras

Cerebras is the **primary provider** for QUASAR - best for tool calling and reliability.

---

## Get API Key

1. Go to [cloud.cerebras.ai](https://cloud.cerebras.ai)
2. Sign up or log in
3. Navigate to API Keys
4. Create a new API key

---

## Configuration

Add to your `.env` file:

```env
CEREBRAS_API_KEY_1=csk_your_key_here
CEREBRAS_API_KEY_2=csk_your_second_key_here
```

---

## Available Models

| Model | Description | Tool Calling |
|-------|-------------|--------------|
| `zai-glm-4.7` | Primary, balanced | ✅ Excellent |
| `qwen-3-235b-a22b-instruct-2507` | Large, powerful | ✅ Excellent |

!!! success "Recommended"
    `zai-glm-4.7` is the default and recommended model.

---

## Usage

```bash
# Auto mode (Cerebras is primary)
quasar "your request"

# Force Cerebras
quasar --model cerebras/zai-glm-4.7 "your request"
```

---

## Why Cerebras?

| Feature | Cerebras | Others |
|---------|----------|--------|
| Tool Calling | ✅ Excellent | ⚠️ Variable |
| Reliability | ✅ High | ⚠️ Variable |
| Speed | ✅ Fast | ✅ Fast |
| Context Length | ✅ Large | ✅ Large |

---

## Rate Limits

Cerebras free tier includes:

- Generous request limits
- High token limits

**Tip:** Add multiple keys for heavy usage:

```env
CEREBRAS_API_KEY_1=csk_first_key
CEREBRAS_API_KEY_2=csk_second_key
```
