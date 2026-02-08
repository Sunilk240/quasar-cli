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
    "my-server": {
      "command": "npx",
      "args": ["-y", "@my-org/mcp-server"]
    },
    "local-server": {
      "command": "python",
      "args": ["-m", "my_mcp_server"]
    }
  }
}
```

---

## Configuration Options

| Field | Description |
|-------|-------------|
| `command` | Executable to run |
| `args` | Command-line arguments |
| `env` | Environment variables (optional) |

---

## Example: DuckDuckGo Search

```json
{
  "mcpServers": {
    "duckduckgo": {
      "command": "npx",
      "args": ["-y", "@anthropic/mcp-duckduckgo"]
    }
  }
}
```

---

## How It Works

1. QUASAR reads `.quasar/mcp.json` on startup
2. Launches each MCP server process
3. Discovers available tools
4. Makes tools available to the AI

```
Startup → Load MCP Config → Launch Servers → Discover Tools
```

---

## Creating MCP Servers

### Python MCP Server

```python
#!/usr/bin/env python
"""Example MCP Server"""

import asyncio
from mcp.server import Server
from mcp.server.stdio import stdio_server
from mcp.types import Tool

server = Server("my-server")

@server.list_tools()
async def list_tools():
    return [
        Tool(
            name="my_tool",
            description="Does something useful",
            inputSchema={
                "type": "object",
                "properties": {
                    "input": {"type": "string"}
                }
            }
        )
    ]

@server.call_tool()
async def call_tool(name: str, arguments: dict):
    if name == "my_tool":
        return {"result": f"Processed: {arguments.get('input')}"}

async def main():
    async with stdio_server() as (read, write):
        await server.run(read, write)

if __name__ == "__main__":
    asyncio.run(main())
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

---

## Troubleshooting

### Server Not Loading

Check the logs:

```bash
# Run QUASAR with debug logging
quasar "test" 2>&1 | grep -i mcp
```

### Tools Not Available

Ensure the server returns valid tools in `list_tools()`.

### Connection Timeout

```json
{
  "mcpServers": {
    "slow-server": {
      "command": "python",
      "args": ["slow_server.py"],
      "timeout": 60
    }
  }
}
```
