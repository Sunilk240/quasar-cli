# CLI Reference

Complete reference for QUASAR command-line options.

---

## Basic Usage

```bash
quasar [OPTIONS] [PROMPT]
```

---

## Arguments

| Argument | Description |
|----------|-------------|
| `PROMPT` | Your request to QUASAR |

---

## Options

### --workspace / -w

Specify the working directory.

```bash
quasar --workspace /path/to/project "your request"
```

Default: Current directory (`.`)

---

### --model / -m

Specify provider and model.

```bash
quasar --model provider/model-name "your request"
```

**Format:** `provider/model-name`

**Examples:**

```bash
quasar --model cerebras/zai-glm-4.7 "create hello.py"
quasar --model groq/openai/gpt-oss-120b "explain main.py"
quasar --model ollama/qwen2.5-coder:7b "fix bug"
```

Default: Auto (Cerebras → Ollama → Groq)

---

### --interactive / -i

Enter interactive REPL mode.

```bash
quasar --interactive
quasar -i
```

Interactive mode allows multiple commands without restarting.

---

### --version / -v

Show version information.

```bash
quasar --version
```

Output:

```
QUASAR v2.0.0 (or higher)
```

---

### --help / -h

Show help message.

```bash
quasar --help
```

---

## Examples

### Single Command

```bash
# Create a file
quasar "create a hello.py that prints Hello World"

# Explain code
quasar "explain what main.py does"

# Search
quasar "find all files with TODO comments"
```

### With Options

```bash
# Specify workspace
quasar -w /projects/myapp "add tests"

# Use specific model
quasar -m groq/openai/gpt-oss-120b "refactor api.py"

# Both options
quasar -w /projects/myapp -m cerebras/zai-glm-4.7 "optimize queries"
```

### Interactive Mode

```bash
quasar -i
> explain main.py
> add error handling
> create tests
> exit
```

---

## Exit Codes

| Code | Meaning |
|------|---------|
| 0 | Success |
| 1 | Error |
| 130 | User interrupt (Ctrl+C) |

---

## Environment Variables

| Variable | Description |
|----------|-------------|
| `GROQ_API_KEY_1` | Groq API key |
| `CEREBRAS_API_KEY_1` | Cerebras API key |
| `TAVILY_API_KEY` | Tavily search key |
| `OLLAMA_BASE_URL` | Ollama server URL |

See [Configuration](../getting-started/configuration.md) for details.
