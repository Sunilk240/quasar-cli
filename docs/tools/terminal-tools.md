# Terminal Tools

2 tools for terminal command suggestions.

---

## suggest_command

Suggests a terminal command for the given task.

```python
suggest_command(task: str) -> str
```

**Examples:**

```
> how do I run the tests?
> install the dependencies
> start the development server
```

**Output:**

```
💡 Suggested command:

pytest tests/ -v

(Copy and run this command yourself)
```

!!! warning "Safety"
    QUASAR **suggests** commands, it does NOT execute them directly.
    This is a safety feature to prevent accidental harm.

---

## check_command_available

Check if a command is available on the system.

```python
check_command_available(command: str) -> bool
```

**Example:**

```
> is docker installed?
```

**Output:**

```
✅ docker is available at /usr/bin/docker
```

or

```
❌ docker is not found in PATH
```

---

## Why Not Execute Directly?

QUASAR doesn't execute commands automatically for safety:

| Risk | Example |
|------|---------|
| Data loss | `rm -rf /` |
| Side effects | `npm publish` |
| Security | `curl | sh` |
| Resource usage | `fork bomb` |

By suggesting instead of executing, you maintain control.

---

## Shell Integration

You can copy suggested commands directly to your shell:

```bash
# QUASAR suggests:
pytest tests/ -v

# You copy and run it yourself
```

Or use your shell's history:

```bash
# After running, it's in your history
!!  # Repeat last command
```
