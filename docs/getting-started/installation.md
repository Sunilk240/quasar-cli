# Installation

Install QUASAR using pip from PyPI.

---

## Requirements

| Requirement | Version |
|-------------|---------|
| Python | 3.10+ |
| pip | Latest |
| OS | Windows, macOS, Linux |

---

## Install from PyPI

```bash
pip install quasar-ai
```

This installs QUASAR and all dependencies including:

- `typer` - CLI framework
- `rich` - Terminal formatting
- `langchain` - AI orchestration
- `langchain-groq`, `langchain-ollama` - Provider integrations

---

## Verify Installation

```bash
quasar --version
```

You should see:

```
QUASAR v2.0.0 (or higher)
```

---

## Upgrade

To upgrade to the latest version:

```bash
pip install --upgrade quasar-ai
```

---

## Development Installation

For development or contributing:

```bash
# Clone the repository
git clone https://github.com/Sunilk240/QUASAR.git
cd QUASAR/quasar-cli

# Install in development mode
pip install -e ".[dev]"
```

---

## Troubleshooting

### Python Version Error

```
ERROR: This package requires Python 3.10 or higher
```

**Solution:** Upgrade Python:

```bash
# Check your Python version
python --version

# Use pyenv or install Python 3.10+
```

### Permission Error

```
ERROR: Could not install packages due to an EnvironmentError
```

**Solution:** Use `--user` flag or virtual environment:

```bash
pip install --user quasar-ai

# Or use virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install quasar-ai
```

---

## Next Steps

After installation, [configure your API keys](configuration.md).
