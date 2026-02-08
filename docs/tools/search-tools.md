# Search Tools

4 tools for finding files and searching content.

---

## find_files

Find files by name pattern.

```python
find_files(pattern: str, directory: str = ".") -> str
```

**Examples:**

```
> find all Python files
> find files named "config*"
> find test files in src/
```

**Patterns:**

- `*.py` - All Python files
- `test_*.py` - Test files
- `**/config.*` - Config files anywhere

---

## search_content

Search for text inside files (like grep).

```python
search_content(query: str, directory: str = ".", file_pattern: str = "*") -> str
```

**Examples:**

```
> search for "TODO" in all files
> find "import asyncio" in Python files
> search for "API_KEY" in config files
```

---

## explore_codebase

Get an overview of the codebase structure.

```python
explore_codebase(directory: str = ".") -> str
```

**Example:**

```
> explore this codebase
```

**Output:**

```
📁 Project Overview
├── src/ (15 files)
│   ├── main.py
│   ├── config.py
│   └── ...
├── tests/ (8 files)
├── docs/ (5 files)
└── requirements.txt
```

---

## list_directory

List contents of a directory.

```python
list_directory(path: str = ".") -> str
```

**Example:**

```
> list files in src/
```

**Output:**

```
📁 src/
├── 📄 main.py (2.5KB)
├── 📄 config.py (1.2KB)
├── 📁 utils/
└── 📁 models/
```
