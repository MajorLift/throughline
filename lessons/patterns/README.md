# Patterns

Technical behaviors, API quirks, domain knowledge — things that are true about systems you work with.

## Format

```markdown
# {Pattern Name}

**Context:** {where this applies}

**Pattern:** {what is true}

**Implication:** {how this affects work}
```

## Examples

- "GitHub API: 'number' is for display, 'id' is the database key — use id for API calls"
- "Our codebase uses barrel exports — import from index, not direct files"
- "PostgreSQL JSONB indexing requires GIN — don't assume B-tree works"
- "This repo's tests are flaky on CI — retry once before investigating"

## Adding Patterns

Create a new file: `{pattern-name}.md`

Or use: `/learn pattern: {description}`