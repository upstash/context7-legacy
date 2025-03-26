# Context7

Instant LLM Context for Agents and Developers

## Overview

Context7 provides a powerful system for creating and managing context libraries that can be used by LLMs, agents, and developers. It extracts, processes, and organizes code snippets from documentation repositories, making them easily accessible as context for AI systems.

## Adding a New Project

To add a new package to Context7, you need to create a JSON file that defines the project's information and send a Pull Request.
When PR is approved and merged, the package will be indexed and be available in Context7 web site and API.

### Project JSON Structure

A Context7 project is defined using the following JSON structure:

```json
{
  "settings": {
    "project": "project-name",
    "title": "Human-Readable Project Title",
    "docsRepoUrl": "https://github.com/organization/repo",
    "folders": ["docs", "src"],
    "excludeFolders": ["node_modules", ".git"]
  },
  "version": {
    "lastUpdate": "2023-03-25T10:04:00Z",
    "totalTokens": 0,
    "totalPages": 0,
    "totalSnippets": 0,
    "averageTokens": 0,
    "parseDuration": 0,
    "state": "initial",
    "errorCount": 0
  }
}
```

### Field Descriptions

#### Settings Object

| Field            | Type     | Required | Description                                                                                                                       |
| ---------------- | -------- | -------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `project`        | string   | Yes      | A unique identifier for the project. Used as the key in the database and for file naming. Should be URL-friendly with no spaces.  |
| `title`          | string   | Yes      | A human-readable title for the project. This will be displayed to users.                                                          |
| `docsRepoUrl`    | string   | Yes      | The URL to the GitHub repository containing the documentation to be processed.                                                    |
| `folders`        | string[] | No       | An optional array of folder paths within the repository to include in processing. If not provided, all folders will be processed. |
| `excludeFolders` | string[] | No       | An optional array of folder paths to exclude from processing. Common examples include "node_modules" and ".git".                  |

#### Version Object

| Field            | Type   | Required | Description                                                                                                                                                              |
| ---------------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `lastUpdate`     | string | Yes      | ISO 8601 timestamp of when the project was last updated.                                                                                                                 |
| `totalTokens`    | number | Yes      | The total number of tokens across all processed snippets. This is set by the system after processing.                                                                    |
| `totalPages`     | number | Yes      | The total number of documentation pages processed. This is set by the system after processing.                                                                           |
| `totalSnippets`  | number | Yes      | The total number of code snippets extracted. This is set by the system after processing.                                                                                 |
| `averageTokens`  | number | Yes      | The average number of tokens per snippet. This is set by the system after processing.                                                                                    |
| `parseDuration`  | number | Yes      | The time in milliseconds it took to parse the documentation. This is set by the system.                                                                                  |
| `state`          | string | Yes      | The current state of the project. Must be one of: "initial", "parsed", "finalized", "error", "invalid_docs", "stop", "delete". New projects should start with "initial". |
| `errorCount`     | number | Yes      | The number of errors encountered during processing. This is set by the system.                                                                                           |
| `validationDate` | string | No       | Optional ISO 8601 timestamp of when the project was last validated.                                                                                                      |

### Project States

- `initial`: The project has been created but not yet processed.
- `parsed`: The project's documentation has been parsed, but not yet finalized.
- `finalized`: The project's documentation has been fully processed and is ready for use.
- `error`: An error occurred during processing.
- `invalid_docs`: The documentation could not be properly parsed.
- `stop`: Processing has been manually stopped.
- `delete`: The project is marked for deletion.

## Exporting Projects

You can export all projects using the exportProjects script:

```bash
npm run export-projects
```

This will export all projects to the `packages` directory, with each project in its own subdirectory and JSON file.

## Environment Setup

Context7 requires a Redis database for storage. Set up your environment variables in a `.env` file:

```
UPSTASH_REDIS_REST_URL=your-redis-url
UPSTASH_REDIS_REST_TOKEN=your-redis-token
```

## License

[Add your license information here]
