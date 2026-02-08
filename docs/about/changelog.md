# Changelog

All notable changes to QUASAR.

---

## [2.0.0] - 2024-02-08

### Added

- **MCP Integration**: Support for Model Context Protocol servers
- **Hooks System**: 5 lifecycle hook points for custom behavior
- **Multiple API Keys**: Auto-rotation on rate limits
- **context.md**: Project-specific AI context
- **Session Memory**: Persistent history and recent files
- **Code Intelligence**: 4 new tools for code analysis
- **Web Tools**: DuckDuckGo, Jina Reader, Wikipedia, arXiv, GitHub search

### Changed

- Improved tool calling reliability
- Better error messages
- Faster startup time
- Updated default models

### Fixed

- Model selection override bug
- Rate limit handling
- Backup creation for all file operations

---

## [1.0.0] - 2024-01-15

### Added

- Initial release
- Multi-provider support (Groq, Cerebras, Ollama)
- 15 built-in tools
- Automatic file backups
- Interactive mode
- Workspace support

---

## Versioning

QUASAR follows [Semantic Versioning](https://semver.org/):

- **MAJOR**: Breaking changes
- **MINOR**: New features (backward compatible)
- **PATCH**: Bug fixes
