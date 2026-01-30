# ChatGPT Setup

Integrate learn commands into ChatGPT.

## Quick Start

1. Go to **Settings > Personalization > Custom Instructions**
2. In "How would you like ChatGPT to respond?", add:

```
When I use /learn followed by a correction, acknowledge it and apply immediately. Classify as:
- Session-only: Current conversation
- Standing preference: Remind me to update custom instructions
- Skill: Offer to document

When I use /postmortem after you make a mistake:
1. State what went wrong
2. Identify root cause
3. Specify concrete mitigation
4. Extract pattern

Every postmortem needs a real mitigation, not just "I'll do better."
```

## With Memory

If ChatGPT Memory is enabled:

1. Standing preferences can be saved to memory
2. Say: "Remember this as a preference"
3. ChatGPT will persist across conversations

## With GPTs

For a custom GPT:

1. Create new GPT
2. In Instructions, paste full contents of `custom-instructions.md`
3. Optionally add knowledge files for learnings storage

## Verification

```
/learn Always explain your reasoning step by step
```

ChatGPT should acknowledge and apply.
