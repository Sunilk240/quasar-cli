# Configuration

Configure QUASAR with API keys and options.

---

## API Keys

QUASAR requires API keys from at least one provider. You can use multiple keys for automatic rotation on rate limits.

### Option 1: Using `.env` file (Recommended)

Create a `.env` file in your project directory:

```env
# Groq (recommended - fast inference)
GROQ_API_KEY_1=gsk_your_key_here
GROQ_API_KEY_2=gsk_your_second_key_here

# Cerebras
CEREBRAS_API_KEY_1=csk_your_key_here
CEREBRAS_API_KEY_2=csk_your_second_key_here

# Ollama runs locally - no API key needed
# Default: http://localhost:11434

# Web Search (optional but recommended)
# QUASAR has multiple web tools with fallback support
# Get free key at: https://tavily.com
TAVILY_API_KEY=tvly_your_key_here
```

### Option 2: Environment Variables

=== "Linux/macOS"

    ```bash
    # Groq
    export GROQ_API_KEY_1="gsk_your_key_here"
    export GROQ_API_KEY_2="gsk_your_second_key_here"

    # Cerebras
    export CEREBRAS_API_KEY_1="csk_your_key_here"
    ```

=== "Windows (CMD)"

    ```bash
    # Temporary (current session only)
    set GROQ_API_KEY_1=gsk_your_key_here
    set CEREBRAS_API_KEY_1=csk_your_key_here

    # Permanent (restart terminal after)
    setx GROQ_API_KEY_1 "gsk_your_key_here"
    setx CEREBRAS_API_KEY_1 "csk_your_key_here"
    ```

=== "Windows (PowerShell)"

    ```powershell
    # Temporary (current session only)
    $env:GROQ_API_KEY_1 = "gsk_your_key_here"
    $env:CEREBRAS_API_KEY_1 = "csk_your_key_here"

    # Permanent
    [System.Environment]::SetEnvironmentVariable("GROQ_API_KEY_1", "gsk_your_key_here", "User")
    ```

---

## Get Free API Keys

| Provider | Free Tier | Link |
|----------|-----------|------|
| **Groq** | ✅ Yes | [console.groq.com](https://console.groq.com) |
| **Cerebras** | ✅ Yes | [cloud.cerebras.ai](https://cloud.cerebras.ai) |
| **Ollama** | ✅ Free (Local) | [ollama.ai](https://ollama.ai) |
| **Tavily** | ✅ Yes | [tavily.com](https://tavily.com) |

---

## Multiple Keys

You can add multiple keys per provider:

```env
GROQ_API_KEY_1=gsk_first_key
GROQ_API_KEY_2=gsk_second_key
GROQ_API_KEY_3=gsk_third_key
```

**Benefits:**

- Automatic rotation on rate limits
- No interruptions during heavy usage
- Seamless failover

---

## Provider Priority

QUASAR uses this default priority:

1. **Cerebras** - Best for tool calling
2. **Ollama** - Local, good fallback
3. **Groq** - Fast, but tool calling issues with some models

You can override with `--model` flag:

```bash
quasar --model groq/openai/gpt-oss-120b "your request"
```

---

## Ollama Configuration

QUASAR uses **cloud models** via Ollama for fast execution.

### Setup

1. Install Ollama from [ollama.ai](https://ollama.ai)
2. Start the server: `ollama serve`
3. Pull the required cloud models:

```bash
# Required for Auto mode
ollama pull glm-4.7:cloud
ollama pull deepseek-v3.1:671b-cloud
ollama pull qwen3-coder:480b-cloud
```

### Default Models

| Model | Description |
|-------|-------------|
| `glm-4.7:cloud` | Default, balanced |
| `deepseek-v3.1:671b-cloud` | Code intelligence |
| `gpt-oss:120b-cloud` | Large, powerful |
| `qwen3-coder:480b-cloud` | Coding focused |

### Custom/Local Models

You can also use any local model with the `--model` flag:

```bash
# Use a custom local model
quasar --model ollama/qwen2.5-coder:7b "your request"
quasar --model ollama/codellama:7b "your request"
```

Default Ollama URL: `http://localhost:11434`

---

## Next Steps

- [Choose your model](../features/model-selection.md)
- [Learn about providers](../providers/index.md)
- [Customize with .quasar/](../quasar-directory/index.md)
