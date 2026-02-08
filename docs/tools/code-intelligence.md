# Code Intelligence

4 tools for analyzing and understanding code.

---

## get_diagnostics

Get diagnostics (errors, warnings) for a file.

```python
get_diagnostics(path: str) -> str
```

**Example:**

```
> check main.py for errors
```

**Output:**

```
📋 Diagnostics for main.py:

⚠️ Line 15: Unused import 'os'
❌ Line 42: Undefined variable 'config'
⚠️ Line 78: Line too long (120 > 88 characters)
```

---

## get_symbols

List all symbols (functions, classes, variables) in a file.

```python
get_symbols(path: str) -> str
```

**Example:**

```
> show symbols in utils.py
```

**Output:**

```
📦 Symbols in utils.py:

Classes:
  - ConfigManager (line 12)
  - DatabasePool (line 45)

Functions:
  - load_config() (line 8)
  - connect() (line 34)
  - cleanup() (line 89)

Variables:
  - DEFAULT_TIMEOUT (line 5)
```

---

## find_definition

Find where a symbol is defined.

```python
find_definition(symbol: str, path: str = None) -> str
```

**Example:**

```
> find definition of ConfigManager
```

**Output:**

```
📍 Definition found:

class ConfigManager in src/config.py:12

    class ConfigManager:
        """Manages application configuration."""
        def __init__(self, path: str):
            ...
```

---

## find_references

Find all references to a symbol.

```python
find_references(symbol: str, path: str = None) -> str
```

**Example:**

```
> find all uses of load_config
```

**Output:**

```
🔗 References to load_config:

1. src/main.py:15
   config = load_config("settings.yaml")

2. src/api/server.py:23
   app_config = load_config(config_path)

3. tests/test_config.py:8
   result = load_config("test.yaml")

Total: 3 references
```

---

## Use Cases

| Tool | When to Use |
|------|-------------|
| `get_diagnostics` | Check for errors before commit |
| `get_symbols` | Understand file structure |
| `find_definition` | Navigate to source |
| `find_references` | Find usage before refactoring |
