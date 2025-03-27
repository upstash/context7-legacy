# Context7

**Instant LLM Context for AI Agents and Developers**

[![Website](https://img.shields.io/badge/Website-context7.com-blue)](https://context7.com)
[![Free Plan](https://img.shields.io/badge/Free_Plan-50_Queries/Day-green)](https://context7.com)
[![GitHub](https://img.shields.io/badge/GitHub-Star_Us-yellow)](https://github.com/upstash/context7)

## What is Context7?

Context7 is a system for generating context documents for Large Language Models (LLMs), AI agents, and developers. It extracts high-quality, focused code snippets from documentation repositories, making them accessible as context for developers and AI agents.

**Features:**

- ✅ Clean, relevant context extracted from the latest documentation
- ✅ Only code snippets and their descriptions - no extraneous text
- ✅ Free for personal use (up to 50 queries per day)
- ✅ MCP Server compatibility (Cursor, Windsurf, etc.)
- ✅ Generate context for any project in minutes
- ✅ Embed Context7 links directly in your documentation pages

## How It Works

Context7 processes documentation repositories through a pipeline:

1. **Document Parsing**: Supports multiple formats:

   - Markdown (`.md`, `.mdx`)
   - Plain text (`.txt`)
   - ReStructuredText (`.rst`)
   - Jupyter Notebooks (`.ipynb`)

2. **Context Extraction**: Extracts code snippets and generates descriptive metadata using LLM models.

3. **Embedding Generation**: Converts code and metadata into vector embeddings for efficient search.

4. **Contextual Retrieval**: Provides relevant code examples on demand via API or web interface.

## Using Context7 in Your Projects

### Generate Context for Your Project

1. Add your project to Context7 using one of the methods below
2. Once processed, your project's documentation will be available as contextual snippets
3. Use our API to integrate these snippets into your applications or development workflow

### Embed Context7 in Your Documentation

Add a Context7 link to your documentation pages to give your users instant access to relevant code examples:

```html
<a href="https://context7.com/p/your-project-name" target="_blank">
  See code examples with Context7
</a>
```

This allows your users to quickly find implementation examples without leaving your documentation.

## Adding Your Project to Context7

### Option 1: Automated Addition (Recommended)

Visit [context7.com/add-package](https://context7.com/add-package) to add your package through our web interface.

### Option 2: Manual Addition via Pull Request

1. Create a JSON file defining your project's information
2. Submit a Pull Request to our repository
3. Once approved and merged, your package will be indexed and available

### Project JSON Schema

```json
{
  "settings": {
    "project": "project-name", // Unique, URL-friendly identifier
    "title": "Human-Readable Title", // Display name
    "docsRepoUrl": "https://github.com/organization/repo",
    "folders": ["docs"], // Optional: specific folders to include
    "excludeFolders": ["archive", "old"] // Optional: folders to exclude
  },
  "version": {
    "lastUpdate": "2023-03-25", // ISO 8601 timestamp
    "totalTokens": 0, // Set by system after processing
    "totalPages": 0, // Set by system after processing
    "totalSnippets": 0, // Set by system after processing
    "averageTokens": 0, // Set by system after processing
    "parseDuration": 0, // Set by system after processing
    "state": "initial", // Initial state for new projects
    "errorCount": 0 // Set by system after processing
  }
}
```

## Project States

| State          | Description                                |
| -------------- | ------------------------------------------ |
| `initial`      | Project created but not yet processed      |
| `parsed`       | Documentation parsed but not finalized     |
| `finalized`    | Fully processed and ready for use          |
| `error`        | Error occurred during processing           |
| `invalid_docs` | Documentation could not be properly parsed |
| `stop`         | Processing manually stopped                |
| `delete`       | Project marked for deletion                |

## API Integration

Context7 provides a simple API to retrieve contextual code snippets for your applications:

```bash
curl -X POST "https://api.context7.com/query" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{"query":"How to use feature X", "project":"your-project-name"}'
```

Visit our [API documentation](https://context7.com/docs/api) for more details.

## Contributing

We welcome contributions! Please check our [contribution guidelines](https://github.com/upstash/context7/blob/main/CONTRIBUTING.md) for more information.

## Issues

Context7 needs your help. Please submit any issues and feature requests [here](https://github.com/upstash/context7/issues/new).

## License

Context7 is available under the [MIT License](https://github.com/upstash/context7/blob/main/LICENSE).
