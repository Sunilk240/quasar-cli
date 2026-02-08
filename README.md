# QUASAR Documentation

This repository contains the documentation website for QUASAR - an AI-powered CLI code editor.

## Live Site

Visit: https://sunilk240.github.io/quasar-cli/

## Local Development

### Prerequisites

- Python 3.10+
- pip

### Setup

```bash
# Install MkDocs Material
pip install mkdocs-material

# Serve locally
mkdocs serve
```

Visit: http://127.0.0.1:8000

### Build

```bash
mkdocs build
```

Output in `site/` directory.

## Deployment

Documentation auto-deploys to GitHub Pages on push to `main` branch via GitHub Actions.

## Structure

```
docs/
├── index.md                    # Home
├── getting-started/            # Installation, Setup
├── providers/                  # Groq, Cerebras, Ollama
├── features/                   # Model selection, Tasks
├── quasar-directory/           # .quasar/ configuration
├── tools/                      # 27 built-in tools
├── api/                        # CLI reference
└── about/                      # Changelog, Contributing
```

## License

MIT
