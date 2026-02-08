# Tools

QUASAR comes with 27 built-in tools for AI-powered coding.

---

## Tool Categories

| Category | Count | Description |
|----------|-------|-------------|
| [File Tools](file-tools.md) | 10 | Read, write, patch files |
| [Search Tools](search-tools.md) | 4 | Find files and content |
| [Web Tools](web-tools.md) | 7 | Web search and URL fetch |
| [Terminal Tools](terminal-tools.md) | 2 | Command suggestions |
| [Code Intelligence](code-intelligence.md) | 4 | Code analysis |

**Total: 27 tools**

---

## How Tools Work

```
User Request → Task Classification → Tool Selection → Execution
```

1. QUASAR classifies your request
2. Selects appropriate tools for the task
3. AI uses tools to complete the request

---

## Tool Calling

QUASAR uses LangChain's tool calling:

- AI decides which tools to use
- Tools are called with structured arguments
- Results are processed and returned

---

## All Tools Overview

### File Operations

| Tool | Description |
|------|-------------|
| `read_file` | Read file contents |
| `read_file_chunk` | Read specific lines |
| `create_file` | Create new file |
| `modify_file` | Modify entire file |
| `patch_file` | Apply partial changes |
| `delete_file` | Delete a file |
| `move_file` | Move/rename file |
| `restore_backup` | Restore from backup |
| `list_backups` | List available backups |
| `show_diff` | Compare with backup |

### Search

| Tool | Description |
|------|-------------|
| `find_files` | Find files by pattern |
| `search_content` | Search inside files |
| `explore_codebase` | Overview of codebase |
| `list_directory` | List directory contents |

### Web

| Tool | Description |
|------|-------------|
| `tavily_search` | Web search via Tavily |
| `duckduckgo_search` | Web search via DuckDuckGo |
| `jina_reader` | Clean webpage content |
| `fetch_url_content` | Fetch any URL |
| `wikipedia_search` | Search Wikipedia |
| `arxiv_search` | Search arXiv papers |
| `github_search` | Search GitHub |

### Terminal

| Tool | Description |
|------|-------------|
| `suggest_command` | Suggest terminal commands |
| `check_command_available` | Check if command exists |

### Code Intelligence

| Tool | Description |
|------|-------------|
| `get_diagnostics` | Get code diagnostics |
| `get_symbols` | List code symbols |
| `find_definition` | Find where defined |
| `find_references` | Find all references |
