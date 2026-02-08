# Ollama

QUASAR uses **cloud models** via Ollama for fast execution and best performance.

---

## Installation

### macOS

```bash
brew install ollama
```

### Linux

```bash
curl -fsSL https://ollama.ai/install.sh | sh
```

### Windows

Download from [ollama.ai/download](https://ollama.ai/download)

---

## Start Ollama

```bash
ollama serve
```

Default URL: `http://localhost:11434`

---

## Pull Cloud Models

QUASAR uses cloud models by default. Pull them for Auto mode:

```bash
# Required for Auto mode
ollama pull glm-4.7:cloud
ollama pull deepseek-v3.1:671b-cloud
ollama pull qwen3-coder:480b-cloud
ollama pull gpt-oss:120b-cloud
```

---

## Available Models

### Cloud Models (Default)

| Model | Description | Tool Calling |
|-------|-------------|--------------|
| `glm-4.7:cloud` | Primary, balanced | ✅ Excellent |
| `deepseek-v3.1:671b-cloud` | Code intelligence | ✅ Excellent |
| `gpt-oss:120b-cloud` | Large, powerful | ✅ Excellent |
| `qwen3-coder:480b-cloud` | Coding focused | ✅ Good |
| `deepseek-v3.2:cloud` | Latest DeepSeek | ✅ Good |

!!! success "Recommended"
    `glm-4.7:cloud` is the default model in Auto mode.

---

## Usage

```bash
# Auto mode (uses cloud models)
quasar "your request"

# Specify a cloud model
quasar --model ollama/glm-4.7:cloud "your request"
quasar --model ollama/deepseek-v3.1:671b-cloud "analyze this code"
```

---

## Custom/Local Models

QUASAR also supports any local model for flexibility:

```bash
# Use custom local models
quasar --model ollama/qwen2.5-coder:7b "your request"
quasar --model ollama/codellama:7b "explain main.py"
quasar --model ollama/deepseek-coder:6.7b "refactor utils.py"
```

### When to Use Local Models

- Cloud model rate limits exceeded
- Offline work required
- Privacy-sensitive tasks
- Experimenting with different models

### Pull Local Models

```bash
ollama pull qwen2.5-coder:7b
ollama pull codellama:7b
ollama pull deepseek-coder:6.7b
```

---

## Configuration

No API key needed! Ollama is detected automatically.

To specify a custom URL:

```env
OLLAMA_BASE_URL=http://localhost:11434
```

---

## Troubleshooting

### Connection Refused

```
Error: Connection refused to http://localhost:11434
```

**Solution:** Start Ollama:

```bash
ollama serve
```

### Model Not Found

```
Error: Model 'xyz' not found
```

**Solution:** Pull the model first:

```bash
ollama pull glm-4.7:cloud
```
