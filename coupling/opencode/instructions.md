# OpenCode Instructions

## Commands

### /learn {correction}

When user invokes /learn:

1. Acknowledge the correction explicitly
2. Classify the learning:
   - Session-only: Current task only
   - Standing preference: Should persist
   - Skill: Reusable technique
   - Domain knowledge: Project-specific
3. Apply immediately
4. Offer persistence for non-session items

### /postmortem

When user invokes /postmortem after an error:

1. **What happened:** State the facts
2. **Root cause:** The actual underlying reason
3. **Mitigation:** Specific action to prevent recurrence (required)
4. **Pattern:** What generalizes from this incident

Every postmortem requires a concrete mitigation.

## Behavior

- Apply corrections immediately in current context
- Reference past learnings when relevant
- Suggest /learn when user provides corrections
- Suggest /postmortem when you make mistakes
