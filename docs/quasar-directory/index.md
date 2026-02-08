# .quasar Directory

The `.quasar/` directory stores project-specific configurations and data.

---

## Structure

```
.quasar/
├── context.md      # Project context for AI
├── memory.json     # Session history
├── mcp.json        # MCP server config
├── hooks/          # Lifecycle hooks
│   ├── example_hook.py.disabled
│   └── your_hook.py
└── backups/        # File backups
    └── *.backup.*
```

---

## Auto-Created

QUASAR automatically creates `.quasar/` when you first run it:

```bash
quasar --workspace /path/to/project "hello"
# Creates .quasar/ with templates
```

---

## Components

| File/Folder | Purpose |
|-------------|---------|
| [context.md](context-md.md) | Tell the AI about your project |
| [mcp.json](mcp-integration.md) | Configure MCP servers |
| [hooks/](hooks-system.md) | Add custom lifecycle hooks |
| [memory.json](memory.md) | Session history |
| `backups/` | Auto-created file backups |

---

## Git Ignore

Add `.quasar/` to `.gitignore` if you don't want to version it:

```gitignore
# QUASAR
.quasar/
```

Or keep it to share project context with your team:

```gitignore
# Keep context, ignore volatile files
.quasar/memory.json
.quasar/backups/
```
