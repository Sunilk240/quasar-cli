# Ollama

Ollama provides **local AI models** - no API key required, runs on your machine.

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

## Pull a Model

```bash
# Recommended for coding
ollama pull qwen2.5-coder:7b

# Other options
ollama pull deepseek-coder:6.7b
ollama pull codellama:7b
```

---

## Configuration

No API key needed! Ollama is detected automatically.

To specify a custom URL:

```env
OLLAMA_BASE_URL=http://localhost:11434
```

---

## Available Models

| Model | Size | Best For |
|-------|------|----------|
| `qwen2.5-coder:7b` | 7B | General coding |
| `deepseek-coder:6.7b` | 6.7B | Code generation |
| `codellama:7b` | 7B | Code understanding |
| `glm-4.7:cloud` | Cloud | QUASAR default |

---

## Usage

```bash
# Use Ollama explicitly
quasar --model ollama/qwen2.5-coder:7b "your request"
```

---

## Advantages

| Feature | Benefit |
|---------|---------|
| **Privacy** | Code never leaves your machine |
| **Offline** | Works without internet |
| **Free** | No API costs |
| **Fast** | Low latency (local) |

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
ollama pull qwen2.5-coder:7b
```

### Slow Performance

Local models need GPU for best performance. If running on CPU:

- Use smaller models (7B)
- Expect slower responses
- Consider cloud providers for heavy usage
