# Session Memory

QUASAR maintains session memory to track history and context.

---

## Location

```
.quasar/
└── memory.json    # Session history
```

---

## Structure

```json
{
  "history": [
    {
      "timestamp": "2024-02-08T10:30:00",
      "query": "create a hello.py file",
      "summary": "Created hello.py with Hello World output"
    },
    {
      "timestamp": "2024-02-08T10:35:00", 
      "query": "add error handling",
      "summary": "Added try-except blocks to main.py"
    }
  ],
  "recent_files": [
    "main.py",
    "hello.py",
    "config.py"
  ]
}
```

---

## What's Stored

| Field | Description |
|-------|-------------|
| `history` | Recent query/summary pairs |
| `recent_files` | Recently accessed files |
| `timestamp` | When each action occurred |

---

## How It's Used

QUASAR uses memory for:

1. **Context Building**: Recent history helps AI understand ongoing work
2. **File Access**: Prioritizes recently touched files
3. **Continuity**: Maintains context across sessions

---

## Memory Limits

To prevent bloat:

- History: Last 20 entries
- Recent files: Last 50 files

Older entries are automatically removed.

---

## Clearing Memory

To reset memory:

```bash
# Delete the file
rm .quasar/memory.json

# Or empty it
echo '{"history": [], "recent_files": []}' > .quasar/memory.json
```

---

## Git Ignore

Memory is typically not version controlled:

```gitignore
# .gitignore
.quasar/memory.json
```

This keeps personal session history private.
