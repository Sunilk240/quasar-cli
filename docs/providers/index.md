# Providers

QUASAR supports multiple AI providers for flexibility and reliability.

---

## Supported Providers

| Provider | Type | Best For | Free Tier |
|----------|------|----------|-----------|
| **Cerebras** | Cloud | Tool calling, reliability | ✅ |
| **Groq** | Cloud | Speed, throughput | ✅ |
| **Ollama** | Local | Privacy, offline use | ✅ |

---

## Provider Priority

QUASAR automatically selects providers in this order:

```
1. Cerebras (best for tool calling)
2. Ollama (local, reliable)
3. Groq (fast, but some tool issues)
```

If a provider fails or hits rate limits, QUASAR automatically falls back to the next.

---

## Override Provider

Use `--model` to specify a provider:

```bash
quasar --model cerebras/zai-glm-4.7 "your request"
quasar --model groq/openai/gpt-oss-120b "your request"
quasar --model ollama/qwen2.5-coder:7b "your request"
```

Format: `provider/model-name`

---

## Quick Links

- [Groq Setup](groq.md)
- [Cerebras Setup](cerebras.md)
- [Ollama Setup](ollama.md)
