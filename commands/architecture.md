---
description: Generate a full architecture diagram of the current project
---

# Architecture Diagram

Analyze the current project and generate a **Mermaid architecture diagram** (`graph TD`).

## Steps

1. Explore the project root to understand the directory structure and identify all major components.
2. Read key configuration files (`package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `docker-compose.yml`, etc.) to determine the tech stack.
3. Identify the main layers: entry points, API/routes, services/business logic, data access/models, external integrations, infrastructure.
4. Trace how these layers communicate (imports, HTTP calls, database queries, message queues).
5. Generate a `graph TD` Mermaid diagram using subgraphs for each logical layer.
6. Label edges with communication protocols or relationship types.

## Output

Return:
- A 2-3 sentence summary of the project architecture.
- A single fenced ` ```mermaid ` code block with the architecture diagram.
- A brief legend if any abbreviations or conventions are used.

**SVG Rendering (mandatory — render-and-validate loop):**
1. `mkdir -p ./codemap-output`
2. Write the Mermaid code to `./codemap-output/architecture.mmd`
3. Run: `npx -y @mermaid-js/mermaid-cli -i ./codemap-output/architecture.mmd -o ./codemap-output/architecture.svg -b transparent`
4. **If rendering fails**: read the error, fix the Mermaid code, overwrite the `.mmd`, re-run step 3. **Repeat until it succeeds.**
5. Once successful: remove the `.mmd` file and report: `SVG saved to ./codemap-output/architecture.svg`

$ARGUMENTS
