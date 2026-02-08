# context.md

The `context.md` file provides project-specific context to the AI.

---

## Purpose

When QUASAR processes your requests, it reads `context.md` and includes it in every prompt. This helps the AI:

- Understand your project structure
- Follow your coding conventions
- Know about important files
- Respect your project rules

---

## Location

```
.quasar/
└── context.md    # ← Your project context
```

---

## Default Template

QUASAR creates a template when initializing:

```markdown
# Project Context

## Description
[Describe your project here]

## Code Style
- [Your coding conventions]
- [Naming patterns]
- [Framework preferences]

## Important Files
- [Key files to know about]

## Common Commands
- [Frequently used commands]

## Project Rules
- [Things the AI should always do]
- [Things the AI should never do]

## Notes
- [Any other context]
```

---

## Example

Here's a real-world example:

```markdown
# Project Context

## Description
FastAPI backend for an e-commerce platform.

## Code Style
- Use type hints for all functions
- Follow PEP 8 strictly
- Use async/await for all API endpoints
- Prefer pydantic models over dictionaries

## Important Files
- `app/main.py` - FastAPI app entry point
- `app/core/config.py` - All configuration
- `app/models/` - SQLAlchemy models
- `app/api/` - API route handlers

## Common Commands
- `uvicorn app.main:app --reload` - Start dev server
- `pytest` - Run tests
- `alembic upgrade head` - Run migrations

## Project Rules
- Never modify migration files directly
- Always add docstrings to functions
- Use environment variables for secrets
- Keep endpoints under 50 lines

## Notes
- Database: PostgreSQL
- Auth: JWT tokens
- Deployment: Docker + Kubernetes
```

---

## How It Works

```
User Request → PromptBuilder reads context.md → AI receives context
```

The context is injected into the system prompt, so the AI sees it before your request.

---

## Best Practices

!!! tip "Be Specific"
    Vague: "Use good code style"
    Specific: "Use type hints, follow PEP 8, max 80 chars per line"

!!! tip "List Key Files"
    Helps the AI find important code quickly

!!! tip "Include Commands"
    AI can suggest correct commands for your project

!!! tip "Set Rules"
    Prevent common mistakes by listing what NOT to do

---

## Sharing Context

To share `context.md` with your team:

```gitignore
# .gitignore
.quasar/memory.json
.quasar/backups/
# Don't ignore context.md - keep it in version control
```
