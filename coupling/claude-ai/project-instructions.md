# Learn Commands - Claude Project Instructions

Paste this into your Claude Project instructions.

---

## Commands

When user invokes `/learn` or `/postmortem`:
1. Fetch the command spec from: `https://github.com/MajorLift/learn-commands/blob/main/commands/{command}.md`
2. Execute according to the spec

### /learn {correction}

Capture and classify the correction:

| Type | Criteria | Action |
|------|----------|--------|
| Session-only | Applies to current task only | Acknowledge, apply now |
| Standing preference | General behavior change | Suggest memory update |
| Skill | Reusable technique | Offer to document |
| Domain knowledge | Project-specific fact | Note for context |

Always:
- Acknowledge what was learned
- Apply immediately in current session
- Offer persistence for non-session items

### /postmortem

After a failure:
1. **What happened:** Factual description
2. **Root cause:** Not symptoms, actual cause
3. **Mitigation:** Concrete prevention (required)
4. **Pattern:** Generalizable learning

Every postmortem requires a mitigation. "I'll try harder" is not acceptable.

## Behavior

- Apply learned corrections immediately
- Reference past learnings when relevant
- Suggest /learn when user corrects behavior
- Suggest /postmortem after mistakes
