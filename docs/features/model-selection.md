# Model Selection

QUASAR supports multiple AI models from different providers.

---

## Auto Mode (Default)

By default, QUASAR automatically selects the best model:

```bash
quasar "your request"
```

**Priority Order:**

1. **Cerebras** - Best for tool calling
2. **Ollama** - Local fallback
3. **Groq** - Cloud fallback

---

## Manual Selection

Use `--model` to specify a model:

```bash
quasar --model provider/model-name "your request"
```

### Examples

```bash
# Cerebras
quasar --model cerebras/zai-glm-4.7 "create a hello.py"

# Groq
quasar --model groq/openai/gpt-oss-120b "explain main.py"

# Ollama (local)
quasar --model ollama/qwen2.5-coder:7b "fix the bug"
```

---

## Available Models

### Cerebras

| Model | Description |
|-------|-------------|
| `zai-glm-4.7` | Default, balanced |
| `qwen-3-235b-a22b-instruct-2507` | Large, powerful |

### Groq

| Model | Description |
|-------|-------------|
| `openai/gpt-oss-120b` | Best for tools |
| `openai/gpt-oss-20b` | Smaller, faster |
| `llama-3.3-70b-versatile` | General purpose |

### Ollama

| Model | Description |
|-------|-------------|
| `glm-4.7:cloud` | Default, balanced |
| `deepseek-v3.1:671b-cloud` | Code intelligence |
| `gpt-oss:120b-cloud` | Large, powerful |
| `qwen3-coder:480b-cloud` | Coding focused |

!!! tip "Custom Models"
    Use `--model ollama/your-model` for any local model.

---

## Fallback Behavior

When using **Auto mode**:

1. Tries primary model
2. If fails (rate limit, error), tries next
3. Continues until success or all fail

When using `--model`:

- Uses only specified model
- No fallback to others
- Fails if model unavailable

---

## Tips

!!! tip "Best for Tool Calling"
    Use `cerebras/zai-glm-4.7` or `groq/openai/gpt-oss-120b`

!!! tip "For Privacy"
    Use `ollama/` models for local processing

!!! tip "For Speed"
    Groq models are fastest for inference
