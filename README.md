# codemap

Generate professional Mermaid diagrams from your codebase with a single command.

## Commands

| Command | Description |
|---|---|
| `/codemap:architecture` | Full system architecture diagram |
| `/codemap:deps` | Module dependency graph with circular dependency detection |
| `/codemap:flow <target>` | Flowchart for a specific function or endpoint |
| `/codemap:er` | Entity-relationship diagram from models/schemas |

## Output

Each command produces:

1. A fenced **Mermaid code block** that renders natively on GitHub, GitLab, Notion, Obsidian, and any Markdown viewer that supports Mermaid.
2. A **rendered SVG file** saved to `./codemap-output/<type>.svg` in your project root.

The SVG is generated via `@mermaid-js/mermaid-cli` and validated automatically — if rendering fails, the plugin reads the error, fixes the Mermaid code, and retries until the SVG is valid.

### Output files

| Command | SVG path |
|---|---|
| `architecture` | `./codemap-output/architecture.svg` |
| `deps` | `./codemap-output/deps.svg` |
| `flow <target>` | `./codemap-output/flow-<target>.svg` |
| `er` | `./codemap-output/er.svg` |

## Prerequisites

- **Node.js** (v18+) with `npx` available in PATH

The plugin uses `npx -y @mermaid-js/mermaid-cli` to render SVGs on-the-fly — no global install needed. If `npx` is not available, install the CLI globally:

```bash
npm install -g @mermaid-js/mermaid-cli
```

## Install

From your terminal, run:

```bash
claude plugin marketplace add mikegazzaruso/codemap
claude plugin install codemap@codemap-marketplace
```

Then restart Claude Code to load the plugin.

## Update

```bash
claude plugin update "codemap@codemap-marketplace"
```

Restart Claude Code after updating.

## Examples

### Architecture

```
/codemap:architecture
```

Produces a `graph TD` diagram showing system layers, components, and communication protocols.

### Dependencies

```
/codemap:deps
```

Produces a `graph LR` diagram mapping inter-module imports. Highlights circular dependencies when found.

### Flow

```
/codemap:flow handleCheckout
```

Produces a `flowchart TD` tracing the execution path of a function, including branches, error handling, and external calls.

### Entity-Relationship

```
/codemap:er
```

Produces an `erDiagram` with entities, attributes, types, and relationship cardinality extracted from your ORM models, migrations, or schema definitions.

## Supported Stacks

Works with any language and framework. The plugin analyzes your project structure, config files, imports, and model definitions regardless of tech stack.

## Author

Mike Gazzaruso

## License

MIT
