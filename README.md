# Context7

**Instant LLM Context for AI Agents and Developers**

[![Website](https://img.shields.io/badge/Website-context7.com-blue)](https://context7.com)
[![Free Plan](https://img.shields.io/badge/Free_Plan-50_Queries/Day-green)](https://context7.com)

## What is Context7?

Context7 is a powerful system for creating, managing, and utilizing context libraries for Large Language Models (LLMs), AI agents, and developers. It automatically extracts high-quality, focused code snippets from documentation repositories, making them immediately accessible as context for AI systems.

**Key Benefits:**

- ✅ Clean, relevant context extracted from the latest documentation
- ✅ Only code snippets and their descriptions - no extraneous text
- ✅ Free for personal use (up to 50 queries per day)
- ✅ MCP Server compatibility (Cursor, Windsurf, etc.)

## How It Works

Context7 processes documentation repositories through a sophisticated pipeline:

1. **Document Parsing**: Supports multiple formats:

   - Markdown (`.md`, `.mdx`)
   - Plain text (`.txt`)
   - ReStructuredText (`.rst`)
   - Jupyter Notebooks (`.ipynb`)

2. **Context Extraction**: Intelligently extracts code snippets and generates descriptive metadata.

3. **Embedding Generation**: Converts code and metadata into vector embeddings for efficient search.

4. **Contextual Retrieval**: Provides relevant code examples on demand via API or web interface.

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
    "lastUpdate": "2023-03-25T10:04:00Z", // ISO 8601 timestamp
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

## Usage Examples

```python
# Python example using Context7 API
import requests

response = requests.get(
    "https://api.context7.com/context",
    params={
        "query": "How to create a new project in FastAPI?",
        "project": "fastapi"
    },
    headers={"Authorization": "Bearer YOUR_API_KEY"}
)

context = response.json()
print(context["snippets"])
```

## Contributing

We welcome contributions to improve Context7! Please check our [Contributing Guidelines](CONTRIBUTING.md) for more information.

## License

Context7 is licensed under [LICENSE NAME]. See the [LICENSE](LICENSE) file for details.
