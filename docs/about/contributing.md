# Contributing

Thank you for your interest in contributing to QUASAR!

---

## Ways to Contribute

- 🐛 Report bugs
- 💡 Suggest features
- 📖 Improve documentation
- 🔧 Submit pull requests

---

## Getting Started

### 1. Fork the Repository

```bash
# Fork on GitHub, then clone
git clone https://github.com/YOUR_USERNAME/quasar-cli.git
cd quasar-cli
```

### 2. Set Up Development Environment

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install in development mode
pip install -e ".[dev]"
```

### 3. Run Tests

```bash
pytest tests/ -v
```

---

## Reporting Bugs

1. Check existing issues first
2. Create a new issue with:
   - Clear title
   - Steps to reproduce
   - Expected vs actual behavior
   - QUASAR version (`quasar --version`)
   - Python version
   - OS

---

## Suggesting Features

1. Check existing feature requests
2. Create an issue describing:
   - The problem you're solving
   - Your proposed solution
   - Alternatives considered

---

## Pull Requests

### Guidelines

1. Create a branch: `git checkout -b feature/your-feature`
2. Make changes
3. Add tests if applicable
4. Run tests: `pytest`
5. Commit: `git commit -m "feat: add feature"`
6. Push: `git push origin feature/your-feature`
7. Open a Pull Request

### Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add new feature
fix: resolve bug
docs: update documentation
refactor: improve code structure
test: add tests
```

---

## Code Style

- Follow PEP 8
- Use type hints
- Add docstrings
- Keep functions under 50 lines

---

## Questions?

- Open a GitHub Discussion
- Check existing issues

Thank you for contributing! 🚀
