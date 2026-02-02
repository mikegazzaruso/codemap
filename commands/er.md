---
description: Generate an entity-relationship diagram from models and schemas
---

# Entity-Relationship Diagram

Analyze the current project's data models and generate a **Mermaid ER diagram** (`erDiagram`).

## Steps

1. Locate all model/schema/entity definitions in the project. Look for:
   - ORM models (Prisma, TypeORM, Sequelize, Django, SQLAlchemy, GORM, Ecto, ActiveRecord, etc.)
   - Database migration files
   - GraphQL type definitions
   - TypeScript/Python/Go interfaces or structs that represent data entities
   - JSON Schema or OpenAPI schema definitions
2. For each entity, extract:
   - Name
   - Key attributes (with types and constraints like PK, FK, unique, nullable)
3. Determine relationships between entities:
   - One-to-one (`||--||`)
   - One-to-many (`||--o{`)
   - Many-to-many (`}o--o{`)
   - Read foreign keys, join tables, and relation decorators to determine cardinality.
4. Generate an `erDiagram` Mermaid block with all entities, attributes, and relationships.

## Output

Return:
- A 2-3 sentence summary of the data model.
- A single fenced ` ```mermaid ` code block with the ER diagram.
- Note any entities that seem disconnected or any missing relationships.

**SVG Rendering (mandatory — render-and-validate loop):**
1. `mkdir -p ./codemap-output`
2. Write the Mermaid code to `./codemap-output/er.mmd`
3. Run: `npx -y @mermaid-js/mermaid-cli -i ./codemap-output/er.mmd -o ./codemap-output/er.svg -b transparent`
4. **If rendering fails**: read the error, fix the Mermaid code, overwrite the `.mmd`, re-run step 3. **Repeat until it succeeds.**
5. Once successful: remove the `.mmd` file and report: `SVG saved to ./codemap-output/er.svg`

$ARGUMENTS
