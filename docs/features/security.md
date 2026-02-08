# Security

QUASAR includes security features to protect sensitive data.

---

## Sensitive File Blocking

QUASAR blocks access to sensitive files:

| Pattern | Description |
|---------|-------------|
| `.env*` | Environment files |
| `*.pem` | SSL/TLS certificates |
| `*.key` | Private keys |
| `*_rsa`, `*_ecdsa` | SSH keys |
| `.git/config` | Git credentials |
| `credentials*` | Credential files |
| `secrets*` | Secret files |
| `*.gpg` | GPG encrypted |
| `.aws/*` | AWS credentials |
| `.ssh/*` | SSH directory |

---

## What Happens?

When you try to read/write sensitive files:

```
> read .env file

⚠️ Access blocked: .env is a sensitive file
```

QUASAR will:

1. **Block** the operation
2. **Report** the blocked attempt
3. **Continue** without accessing the file

---

## Command Suggestions

QUASAR **suggests** commands, not executes them:

```
> run npm install

💡 Suggested command:
npm install

(Copy and run this command yourself)
```

This prevents:

- Accidental data loss
- Unintended side effects
- Security vulnerabilities

---

## Workspace Isolation

QUASAR operates within the specified workspace:

```bash
quasar --workspace /path/to/project "your request"
```

- Cannot access files outside workspace
- Cannot traverse up directories
- Respects project boundaries

---

## Best Practices

!!! warning "Never Commit Secrets"
    Keep `.env` files in `.gitignore`:
    ```gitignore
    .env
    .env.local
    .env.*.local
    ```

!!! tip "Use Environment Variables"
    Set API keys as environment variables:
    ```bash
    export GROQ_API_KEY_1="gsk_..."
    ```

!!! tip "Review Before Running"
    Always review QUASAR's suggested commands before executing them.

---

## Reporting Issues

If you find a security issue:

1. Do NOT open a public issue
2. Email: [security contact]
3. Include reproduction steps
