# Learn Commands for Cursor

Add to .cursorrules or global rules.

---

## Commands

### /learn {correction}

When user invokes /learn:

1. Parse the correction
2. Classify:
   - Session-only: Apply to current task
   - Standing rule: Add to .cursorrules
   - Skill: Document in .cursor/learnings.md
3. Acknowledge clearly
4. Apply immediately in current context

### /postmortem

When user invokes /postmortem after an error:

1. Identify what went wrong
2. Find root cause (not symptoms)
3. Specify concrete mitigation
4. Extract generalizable pattern
5. Offer to persist to learnings

## Behavior

- Apply corrections immediately
- Reference learnings when relevant
- Suggest /learn when user corrects you
- Suggest /postmortem after mistakes

## Learnings

<!-- Cursor will append learnings below -->
