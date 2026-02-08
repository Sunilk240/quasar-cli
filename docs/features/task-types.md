# Task Types

QUASAR classifies your requests into 6 task types, each with optimized tools.

---

## Task Categories

| Task Type | Description | Primary Tools |
|-----------|-------------|---------------|
| `file_operations` | Create, edit, delete files | File + Search |
| `search` | Find files and content | Search + File |
| `execution` | Run commands | Terminal + File + Search |
| `web` | Web search and URLs | Web + File + Search |
| `code_intelligence` | Analyze code | Code Intel + File + Search |
| `chat` | General conversation | All except Terminal |

---

## How It Works

```
User Request → Task Classification → Tool Selection → Execution
```

1. **Classification**: QUASAR analyzes your request
2. **Tool Selection**: Assigns appropriate tools
3. **Execution**: Runs tools to complete task

---

## Task Details

### file_operations

Creates, modifies, or deletes files.

**Triggers:**

- "create a file..."
- "add to config.py..."
- "delete old.py..."
- "refactor utils.py..."

**Tools:** `FILE_TOOLS + SEARCH_TOOLS`

---

### search

Finds files and searches content.

**Triggers:**

- "find files with..."
- "search for 'TODO'..."
- "list all Python files..."

**Tools:** `SEARCH_TOOLS + FILE_TOOLS`

---

### execution

Suggests terminal commands.

**Triggers:**

- "how do I run tests?"
- "install dependencies..."
- "start the server..."

**Tools:** `TERMINAL_TOOLS + FILE_TOOLS + SEARCH_TOOLS`

!!! note "Safety"
    QUASAR **suggests** commands, not executes them directly.

---

### web

Searches the web and fetches URLs.

**Triggers:**

- "search for Python best practices..."
- "what is FastAPI?"
- "fetch the README from..."

**Tools:** `WEB_TOOLS + FILE_TOOLS + SEARCH_TOOLS`

---

### code_intelligence

Analyzes and understands code.

**Triggers:**

- "explain main.py..."
- "find definition of..."
- "show references to..."

**Tools:** `CODE_INTELLIGENCE_TOOLS + FILE_TOOLS + SEARCH_TOOLS`

---

### chat

General conversation and questions.

**Triggers:**

- "what is..."
- "explain..."
- (anything not matching other types)

**Tools:** All except Terminal
