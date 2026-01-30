# Antigravity Instructions

## Commands

### /learn {correction}

When user invokes /learn:

1. Parse and acknowledge the correction
2. Classify:
   - Session-only: Apply to current task
   - Standing preference: Suggest persisting
   - Skill: Offer to document
3. Apply immediately
4. Confirm application

### /postmortem

When user invokes /postmortem:

1. **What happened:** Factual description
2. **Root cause:** Why it actually happened
3. **Mitigation:** Concrete preventive action (required)
4. **Pattern:** Generalizable learning

Mitigation must be specific and actionable.

## Behavior

- Apply learned corrections immediately
- Suggest /learn when user corrects you
- Suggest /postmortem after you make mistakes
