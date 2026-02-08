# QUASAR - AI-Powered CLI Code Editor

<div align="center">
  <h2>🚀 Your Intelligent Coding Assistant in the Terminal</h2>
</div>

QUASAR is an AI-powered command-line code editor that can understand your codebase, generate code, fix bugs, and execute tasks using AI.

---

## ✨ Features

<div class="grid cards" markdown>

-   :material-robot: **Intelligent AI Agent**

    Understands context, plans tasks, and executes with 27+ tools

-   :material-server: **Multiple Providers**

    Supports Groq, Cerebras, and local Ollama models

-   :material-cog: **MCP Integration**

    Extend capabilities with Model Context Protocol servers

-   :material-hook: **Custom Hooks**

    Add your own lifecycle hooks for custom behavior

-   :material-backup-restore: **Auto Backup**

    Automatic file backups before every modification

-   :material-shield-lock: **Secure**

    Blocks access to sensitive files like .env and SSH keys

</div>

---

## 🚀 Quick Start

```bash
# Install QUASAR
pip install quasar-ai

# Set your API key
export GROQ_API_KEY_1="gsk_your_key_here"

# Run QUASAR
quasar "create a hello.py file that prints Hello World"
```

---

## 📖 Documentation Overview

| Section | Description |
|---------|-------------|
| [Getting Started](getting-started/index.md) | Installation, setup, and first steps |
| [Providers](providers/index.md) | Configure Groq, Cerebras, or Ollama |
| [Features](features/index.md) | Model selection, task types, backups |
| [.quasar Directory](quasar-directory/index.md) | context.md, MCP, hooks, memory |
| [Tools](tools/index.md) | 27 built-in tools for coding tasks |
| [API Reference](api/cli-reference.md) | CLI flags and options |

---

## 🎯 Why QUASAR?

| Feature | QUASAR | Traditional CLI |
|---------|--------|-----------------|
| AI-Powered | ✅ | ❌ |
| Multi-Provider | ✅ | ❌ |
| Auto Backup | ✅ | ❌ |
| Extensible (MCP) | ✅ | ❌ |
| Custom Hooks | ✅ | ❌ |
| Tool Calling | ✅ 27 tools | ❌ |

---

## 📦 Installation

```bash
pip install quasar-ai
```

**Requirements:**

- Python 3.10+
- API key from Groq, Cerebras, or local Ollama

[Get Started →](getting-started/installation.md){ .md-button .md-button--primary }
