# MCP Integration

QUASAR supports the Model Context Protocol (MCP) for extending capabilities.

---

## What is MCP?

MCP (Model Context Protocol) is a standard for connecting AI agents to external tools and services. QUASAR can load MCP servers to add new tools.

---

## Configuration

Configure MCP servers in `.quasar/mcp.json`:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "package-name"]
    }
  }
}
```

### Configuration Options

| Field | Description |
|-------|-------------|
| `command` | Executable to run (`npx`, `python`, etc.) |
| `args` | Command-line arguments |
| `env` | Environment variables (optional) |
| `cwd` | Working directory (optional, defaults to workspace) |
| `disabled` | Set to `true` to skip this server |

---

## Example: DuckDuckGo Search

Add web search capability using DuckDuckGo:

```json
{
  "mcpServers": {
    "duckduckgo": {
      "command": "npx",
      "args": ["-y", "duckduckgo-mcp-server"]
    }
  }
}
```

Then use it:

```
> search for "Python async tutorial"
```

---

## Creating Custom MCP Servers

### Simple Python MCP Server

Create `.quasar/my_server.py`:

```python
#!/usr/bin/env python3
"""Simple MCP Server - implements JSON-RPC protocol directly"""

import sys
import json
from datetime import datetime


def send_response(response: dict):
    """Send JSON-RPC response to stdout."""
    print(json.dumps(response), flush=True)


def handle_request(request: dict) -> dict:
    """Handle incoming JSON-RPC request."""
    method = request.get("method", "")
    params = request.get("params", {})
    request_id = request.get("id")
    
    # Initialize
    if method == "initialize":
        return {
            "jsonrpc": "2.0",
            "id": request_id,
            "result": {
                "protocolVersion": "2024-11-05",
                "capabilities": {"tools": {}},
                "serverInfo": {"name": "my-server", "version": "1.0.0"}
            }
        }
    
    # List tools
    elif method == "tools/list":
        return {
            "jsonrpc": "2.0",
            "id": request_id,
            "result": {
                "tools": [
                    {
                        "name": "echo",
                        "description": "Echoes back the input message",
                        "inputSchema": {
                            "type": "object",
                            "properties": {
                                "message": {"type": "string", "description": "Message to echo"}
                            },
                            "required": ["message"]
                        }
                    },
                    {
                        "name": "get_time",
                        "description": "Returns current date and time",
                        "inputSchema": {"type": "object", "properties": {}}
                    }
                ]
            }
        }
    
    # Call tool
    elif method == "tools/call":
        tool_name = params.get("name", "")
        arguments = params.get("arguments", {})
        
        if tool_name == "echo":
            message = arguments.get("message", "")
            result_text = f"Echo: {message}"
        elif tool_name == "get_time":
            result_text = f"Current time: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}"
        else:
            return {
                "jsonrpc": "2.0", "id": request_id,
                "error": {"code": -32601, "message": f"Unknown tool: {tool_name}"}
            }
        
        return {
            "jsonrpc": "2.0",
            "id": request_id,
            "result": {"content": [{"type": "text", "text": result_text}]}
        }
    
    # Unknown method
    else:
        return {
            "jsonrpc": "2.0", "id": request_id,
            "error": {"code": -32601, "message": f"Method not found: {method}"}
        }


def main():
    """Main loop - read requests from stdin, send responses to stdout."""
    for line in sys.stdin:
        line = line.strip()
        if not line:
            continue
        try:
            request = json.loads(line)
            response = handle_request(request)
            send_response(response)
        except Exception as e:
            send_response({"jsonrpc": "2.0", "id": None, "error": {"code": -32603, "message": str(e)}})


if __name__ == "__main__":
    main()
```

### Register in mcp.json

```json
{
  "mcpServers": {
    "my-server": {
      "command": "python",
      "args": ["path/to/my_server.py"]
    }
  }
}
```

### Use Your Server

```
> echo hello world
> what time is it?
```

---

## How It Works

```
Startup → Load .quasar/mcp.json → Launch Servers → Discover Tools → Ready
```

1. QUASAR reads `.quasar/mcp.json` on startup
2. Launches each MCP server as a subprocess
3. Sends `initialize` and `tools/list` requests
4. Makes discovered tools available to the AI

---

## Troubleshooting

### Server Not Loading

Check the logs in `backend/logs/agent_*.log` for MCP errors.

### "File not found" Error

- On Windows, use `npx.cmd` or let QUASAR auto-detect
- For Python scripts, use relative paths from workspace

### Tools Not Working

Ensure your server:
- Reads from stdin line by line
- Writes JSON responses to stdout
- Flushes output after each response
