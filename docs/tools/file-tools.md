# File Tools

10 tools for file operations.

---

## read_file

Read entire file contents.

```python
read_file(path: str) -> str
```

**Example:**

```
> read main.py
```

---

## read_file_chunk

Read specific lines from a file.

```python
read_file_chunk(path: str, start_line: int, end_line: int) -> str
```

**Example:**

```
> show lines 10-50 of main.py
```

---

## create_file

Create a new file with content.

```python
create_file(path: str, content: str) -> str
```

**Example:**

```
> create a config.yaml file with default settings
```

!!! note "Backup"
    Creates backup if file exists and is overwritten.

---

## modify_file

Replace entire file content.

```python
modify_file(path: str, content: str) -> str
```

**Example:**

```
> replace main.py with async version
```

!!! note "Backup"
    Creates backup before modification.

---

## patch_file

Apply partial changes using find/replace.

```python
patch_file(path: str, find: str, replace: str) -> str
```

**Example:**

```
> change print("hello") to print("world") in main.py
```

!!! tip "Preferred"
    Use `patch_file` instead of `modify_file` for small changes. It's safer and more precise.

---

## delete_file

Delete a file.

```python
delete_file(path: str) -> str
```

**Example:**

```
> delete old_config.py
```

!!! note "Backup"
    Creates backup before deletion.

---

## move_file

Move or rename a file.

```python
move_file(source: str, destination: str) -> str
```

**Example:**

```
> rename utils.py to helpers.py
```

---

## restore_backup

Restore file from backup.

```python
restore_backup(path: str, timestamp: str = None) -> str
```

**Example:**

```
> restore main.py from last backup
```

---

## list_backups

List available backups for a file.

```python
list_backups(path: str) -> str
```

**Example:**

```
> show backups for config.py
```

---

## show_diff

Show differences between current and backup.

```python
show_diff(path: str, timestamp: str = None) -> str
```

**Example:**

```
> show diff for main.py
```

Output:

```diff
- old_function()
+ new_function()
  unchanged_line()
```
