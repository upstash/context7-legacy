# Context7

NOTE: This repo will be moved to [https://github.com/upstash/context7-mcp](https://github.com/upstash/context7-mcp)

Instant LLM Context for AI Agents and Developers

[![Website](https://img.shields.io/badge/Website-context7.com-blue)](https://context7.com) [![MCP Server](https://img.shields.io/badge/MCP_Server-context7--mcp-green)](https://github.com/upstash/context7-mcp)

---

## What is Context7?

Context7 is a robust platform designed to create, manage, and leverage context libraries for Large Language Models (LLMs), AI agents, and developers. It automatically pulls high-quality, targeted code snippets from documentation repositories, delivering them as ready-to-use context for AI systems. Built by the Upstash team, you can enjoy Context7 with confidence knowing it’s backed by proven expertise.

**Key Benefits:**  
✅ **Precise Context:** Extracts clean, relevant snippets from up-to-date documentation  
✅ **Focused Content:** Includes only code and descriptions—no fluff or filler  
✅ **Free Tier:** Up to 50 queries per day for personal use at no cost  
✅ **Broad Compatibility:** Works seamlessly with MCP servers (e.g., Cursor, Windsurf)  
✅ **Fast Integration:** Generate library-specific context in minutes and embed Context7 links directly into your documentation

---

## How It Works

Context7 transforms documentation into actionable context through a streamlined pipeline:

1. **Document Parsing**: Supports a variety of formats:

   - Markdown (`.md`, `.mdx`)
   - Plain Text (`.txt`)
   - ReStructuredText (`.rst`)
   - Jupyter Notebooks (`.ipynb`)

2. **Context Extraction**: Uses LLM models to pull code snippets and craft concise, descriptive metadata.

3. **Embedding Generation**: Converts snippets and metadata into vector embeddings for fast, accurate retrieval.

4. **Contextual Retrieval**: Delivers relevant code examples instantly via API or web interface.

---

## Using Context7

### Generate Context for Your Library

1. Add your library to Context7 using one of the methods below.
2. Once processed, access your documentation as contextual snippets.
3. Refine results by searching topics and adjusting token size as needed.

### Embed Context7 in Your Documentation

Boost your docs with instant code examples by adding a Context7 link:

```html
<a href="https://context7.com/YOUR_LIBRARY/llms.txt?tokenLimit=MAX_TOKEN_LIMIT" target="_blank">
  See llms.txt with code examples
</a>
```

This keeps users in your documentation while giving them quick access to implementation snippets.

---

## Adding Your Library to Context7

### Option 1: Automated Addition (Recommended)

Head to [context7.com/add-library](https://context7.com/add-library) and add your library via our simple web interface.

### Option 2: Manual Addition via Pull Request

1. Create a JSON file with your library details (see schema below).
2. Submit a Pull Request to our repository.
3. Once approved and merged, your library will be indexed and available.

> [!IMPORTANT]  
> Ensure the repo includes the documentation files of the library with md/mdx/txt/rst/ipynb format.

### Library JSON Schema

```json
{
  "settings": {
    "library": "library-name", // Unique, URL-friendly identifier
    "title": "Human-Readable Title", // Display name
    "docsRepoUrl": "https://github.com/organization/repo",
    "folders": ["docs"], // Optional: folders to include
    "excludeFolders": ["archive", "old"] // Optional: folders to exclude
  },
  "version": {
    "lastUpdate": "2023-03-25", // ISO 8601 timestamp
    "totalTokens": 0, // Set by system after processing
    "totalPages": 0, // Set by system after processing
    "totalSnippets": 0, // Set by system after processing
    "averageTokens": 0, // Set by system after processing
    "parseDuration": 0, // Set by system after processing
    "state": "initial", // Initial state for new libraries
    "errorCount": 0 // Set by system after processing
  }
}
```

---

## Library States

| State          | Description                             |
| -------------- | --------------------------------------- |
| `initial`      | Library created, not yet processed      |
| `parsed`       | Documentation parsed, not yet finalized |
| `finalized`    | Fully processed and ready to use        |
| `error`        | Processing hit an error                 |
| `invalid_docs` | Docs couldn’t be parsed correctly       |
| `stop`         | Processing halted manually              |
| `delete`       | Library slated for removal              |

---

## API Integration

Coming soon!

---

## Contributing

We’d love your input! See our [contribution guidelines](https://github.com/upstash/context7/blob/main/CONTRIBUTING.md) to get started.

---

## Issues

Help us improve by reporting bugs or suggesting features [here](https://github.com/upstash/context7/issues/new).
