---
description: Generate a module dependency graph for the current project
---

# Dependency Graph

Analyze the current project and generate a **Mermaid dependency graph** (`graph LR`).

## Steps

1. Explore the project structure and identify all modules, packages, or major directories.
2. For each module, read source files and trace `import`/`require`/`use`/`include` statements to map inter-module dependencies.
3. Identify dependency direction (who depends on whom).
4. Detect circular dependencies if any exist.
5. Generate a `graph LR` Mermaid diagram showing module-to-module relationships.
6. Use subgraphs to group modules by layer or domain if the project is large.
7. If circular dependencies are found, highlight them with a red/dashed style and call them out explicitly.

## Output

Return:
- A 2-3 sentence summary of the dependency structure.
- A single fenced ` ```mermaid ` code block with the dependency graph.
- Call out any circular dependencies or tightly coupled areas.

**SVG Rendering (mandatory — render-and-validate loop):**
1. `mkdir -p ./codemap-output`
2. Write the Mermaid code to `./codemap-output/deps.mmd`
3. Run: `npx -y @mermaid-js/mermaid-cli -i ./codemap-output/deps.mmd -o ./codemap-output/deps.svg -b transparent`
4. **If rendering fails**: read the error, fix the Mermaid code, overwrite the `.mmd`, re-run step 3. **Repeat until it succeeds.**
5. Once successful: remove the `.mmd` file and report: `SVG saved to ./codemap-output/deps.svg`

$ARGUMENTS
