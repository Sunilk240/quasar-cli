# Quick Start

Get started with QUASAR in under 5 minutes.

---

## Prerequisites

- QUASAR installed (`pip install quasar-ai`)
- API key configured (see [Configuration](configuration.md))

---

## Your First Command

```bash
quasar "create a hello.py file that prints Hello World"
```

QUASAR will:

1. 🧠 Understand your request
2. 📝 Create the file
3. ✅ Report what was done

---

## Interactive Mode

For multiple commands, use interactive mode:

```bash
quasar
# or
quasar --interactive
```

You'll see a prompt:

```
> 
```

Now you can chat with QUASAR:

```
> explain main.py
> fix the bug in utils.py
> create tests for api.py
```

Type `exit` or `quit` to leave.

---

## Common Commands

### File Operations

```bash
quasar "create a config.py with database settings"
quasar "add error handling to main.py"
quasar "refactor utils.py to use async"
```

### Code Understanding

```bash
quasar "explain what server.py does"
quasar "find all files using asyncio"
quasar "show me the database models"
```

### Search & Navigation

```bash
quasar "find files with TODO comments"
quasar "search for 'API_KEY' in config files"
quasar "list all Python files in src/"
```

### Terminal Commands

```bash
quasar "how do I run the tests?"
quasar "install the dependencies"
quasar "start the development server"
```

---

## Specify Workspace

By default, QUASAR uses the current directory. To specify a different workspace:

```bash
quasar --workspace /path/to/project "your request"
```

---

## Next Steps

- [Configure API keys](configuration.md)
- [Learn about model selection](../features/model-selection.md)
- [Explore all tools](../tools/index.md)
