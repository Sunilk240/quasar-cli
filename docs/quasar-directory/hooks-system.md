# Hooks System

QUASAR supports lifecycle hooks for custom behavior at key points.

---

## What are Hooks?

Hooks are Python functions that run at specific points in QUASAR's workflow:

- Before/after tool execution
- On errors
- On task completion
- Before sending responses

---

## Hook Points

| Hook Point | When It Runs |
|------------|--------------|
| `PRE_TOOL_USE` | Before any tool is called |
| `POST_TOOL_USE` | After any tool completes |
| `ON_ERROR` | When an error occurs |
| `ON_COMPLETE` | When task completes |
| `PRE_RESPONSE` | Before sending response to user |

---

## Location

```
.quasar/
└── hooks/
    ├── example_hook.py.disabled    # Template (disabled)
    └── my_hook.py                  # Active hook
```

Files ending in `.disabled` are not loaded.

---

## Creating a Hook

### 1. Create Hook File

Create `.quasar/hooks/my_hook.py`:

```python
from services.agent.hooks import hook, HookPoint, HookResult

@hook(HookPoint.PRE_TOOL_USE)
def before_tool(context):
    """Runs before every tool call."""
    tool_name = context.get("tool_name")
    print(f"🔧 About to use: {tool_name}")
    
    return HookResult(allow=True)
```

### 2. Restart QUASAR

Hooks are loaded on startup.

---

## Hook Examples

### Block Dangerous Operations

```python
@hook(HookPoint.PRE_TOOL_USE)
def block_delete(context):
    """Block file deletions."""
    tool_name = context.get("tool_name")
    
    if tool_name == "delete_file":
        return HookResult(
            allow=False,
            message="⚠️ File deletion blocked by hook"
        )
    
    return HookResult(allow=True)
```

### Log All Tool Calls

```python
import logging

logger = logging.getLogger("hook")

@hook(HookPoint.POST_TOOL_USE)
def log_tools(context):
    """Log all tool calls."""
    tool_name = context.get("tool_name")
    result = context.get("result")
    
    logger.info(f"Tool: {tool_name}")
    logger.info(f"Result: {result[:100]}...")
    
    return HookResult(allow=True)
```

### Notify on Errors

```python
@hook(HookPoint.ON_ERROR)
def notify_error(context):
    """Send notification on errors."""
    error = context.get("error")
    
    # Send to Slack, email, etc.
    send_notification(f"QUASAR Error: {error}")
    
    return HookResult(allow=True)
```

### Modify Tool Arguments

```python
@hook(HookPoint.PRE_TOOL_USE)
def auto_workspace(context):
    """Add workspace to all file operations."""
    tool_name = context.get("tool_name")
    args = context.get("args", {})
    
    if tool_name in ["create_file", "modify_file"]:
        # Add prefix to all paths
        if "path" in args:
            args["path"] = f"/workspace/{args['path']}"
            return HookResult(
                allow=True,
                modified_args=args
            )
    
    return HookResult(allow=True)
```

---

## HookResult

| Field | Type | Description |
|-------|------|-------------|
| `allow` | bool | If False, blocks the action |
| `modified_args` | dict | Modified arguments to pass |
| `message` | str | Message to log/display |

---

## Async Hooks

Hooks can be async:

```python
@hook(HookPoint.POST_TOOL_USE)
async def async_hook(context):
    """Async hook example."""
    await some_async_operation()
    return HookResult(allow=True)
```

---

## Enabling/Disabling

- Rename to `.disabled` to disable:
  ```bash
  mv my_hook.py my_hook.py.disabled
  ```

- Remove `.disabled` to enable:
  ```bash
  mv my_hook.py.disabled my_hook.py
  ```
