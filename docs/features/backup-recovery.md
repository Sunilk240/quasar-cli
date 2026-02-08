# Backup & Recovery

QUASAR automatically backs up files before modifying them.

---

## How It Works

```
Edit Request → Backup Original → Apply Changes → Success
```

Every time QUASAR modifies a file:

1. **Backup**: Original saved to `.quasar/backups/`
2. **Modify**: Changes applied to file
3. **Confirm**: Success reported

---

## Backup Location

```
.quasar/
└── backups/
    ├── main.py.backup.2024-02-08T10-30-00
    ├── config.py.backup.2024-02-08T10-35-15
    └── utils.py.backup.2024-02-08T11-00-22
```

Filename format: `{original}.backup.{timestamp}`

---

## List Backups

Ask QUASAR:

```
> list backups for main.py
```

Or use the tool directly:

```python
# From QUASAR's tools
list_backups("main.py")
```

---

## Restore Backup

Ask QUASAR:

```
> restore main.py from last backup
```

Or specify a timestamp:

```
> restore main.py from backup 2024-02-08T10-30-00
```

---

## View Diff

Compare current with backup:

```
> show diff for main.py vs last backup
```

QUASAR will show:

```diff
- old line
+ new line
  unchanged line
```

---

## Automatic Behavior

| Action | Backup Created? |
|--------|-----------------|
| `create_file` | ❌ No (new file) |
| `modify_file` | ✅ Yes |
| `patch_file` | ✅ Yes |
| `delete_file` | ✅ Yes |
| `move_file` | ✅ Yes |

---

## Retention

By default, backups are retained indefinitely. To clean up:

```bash
# Manual cleanup
rm -rf .quasar/backups/*

# Or ask QUASAR
> delete backups older than 7 days
```

---

## Best Practices

!!! tip "Before Major Changes"
    QUASAR creates backups automatically, but for major refactors, consider using git:
    ```bash
    git add -A && git commit -m "backup before refactor"
    ```

!!! tip "Check Backups"
    Periodically review your backups folder size:
    ```bash
    du -sh .quasar/backups/
    ```
