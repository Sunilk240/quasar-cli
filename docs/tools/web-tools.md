# Web Tools

7 tools for web search and URL fetching.

---

## tavily_search

Search the web using Tavily API.

```python
tavily_search(query: str, max_results: int = 5) -> str
```

**Examples:**

```
> search for "Python async best practices"
> find tutorials on FastAPI
```

!!! note "API Key Required"
    Set `TAVILY_API_KEY` in your `.env` file.
    Get a free key at [tavily.com](https://tavily.com)

---

## duckduckgo_search

Search using DuckDuckGo (no API key needed).

```python
duckduckgo_search(query: str, max_results: int = 5) -> str
```

**Example:**

```
> search DuckDuckGo for "Python logging"
```

---

## jina_reader

Extract clean content from a webpage.

```python
jina_reader(url: str) -> str
```

**Example:**

```
> read the content of https://example.com/article
```

Returns: Clean, formatted text content.

---

## fetch_url_content

Fetch raw content from any URL.

```python
fetch_url_content(url: str) -> str
```

**Example:**

```
> fetch https://api.example.com/data.json
```

---

## wikipedia_search

Search Wikipedia articles.

```python
wikipedia_search(query: str) -> str
```

**Example:**

```
> search Wikipedia for "Machine Learning"
```

---

## arxiv_search

Search arXiv for academic papers.

```python
arxiv_search(query: str, max_results: int = 5) -> str
```

**Example:**

```
> find papers on "transformer architecture"
```

---

## github_search

Search GitHub repositories and code.

```python
github_search(query: str, search_type: str = "repositories") -> str
```

**Search Types:**

- `repositories` - Find repos
- `code` - Find code snippets

**Example:**

```
> search GitHub for Python CLI frameworks
```

---

## Fallback Behavior

QUASAR tries multiple web tools in sequence:

```
1. Tavily (if API key)
2. DuckDuckGo
3. Jina Reader
```

If one fails, it automatically tries the next.
