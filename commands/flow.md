---
description: Generate a flowchart for a specific function or endpoint
argument-hint: <function name, endpoint, or file:line>
---

# Flow Diagram

Analyze the specified function, endpoint, or code path and generate a **Mermaid flowchart** (`flowchart TD`).

## Target

The user wants a flow diagram for: **$ARGUMENTS**

## Steps

1. Locate the target function, endpoint, or code path in the codebase.
2. Read the implementation and trace the execution flow from entry to exit.
3. Map out:
   - Entry point (request, function call, event trigger)
   - Conditional branches (if/else, switch, guards)
   - Loops and iterations
   - Error handling paths (try/catch, error returns)
   - External calls (database, API, file system)
   - Return/response points
4. Generate a `flowchart TD` Mermaid diagram.
5. Use appropriate shapes:
   - `([...])` for start/end (stadium shape)
   - `{...}` for decisions (diamond)
   - `[...]` for processes (rectangle)
   - `[(...)]` for database operations (cylinder)

## Output

Return:
- A 2-3 sentence summary of what this code path does.
- A single fenced ` ```mermaid ` code block with the flowchart.
- Note any edge cases or error paths that are particularly important.

**SVG Rendering (mandatory — render-and-validate loop):**
1. Derive a slug from the target name (e.g., `handleLogin` → `flow-handleLogin`, `POST /api/users` → `flow-post-api-users`)
2. `mkdir -p ./codemap-output`
3. Write the Mermaid code to `./codemap-output/flow-<target>.mmd`
4. Run: `npx -y @mermaid-js/mermaid-cli -i ./codemap-output/flow-<target>.mmd -o ./codemap-output/flow-<target>.svg -b transparent`
5. **If rendering fails**: read the error, fix the Mermaid code, overwrite the `.mmd`, re-run step 4. **Repeat until it succeeds.**
6. Once successful: remove the `.mmd` file and report: `SVG saved to ./codemap-output/flow-<target>.svg`
