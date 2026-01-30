# Claude.ai Setup

Integrate learn commands into Claude.ai (web/mobile/desktop).

## Quick Start

1. Go to **Settings > Profile > User Preferences**
2. Add:

```
When I use /learn or /postmortem, fetch and execute the command from:
https://github.com/MajorLift/learn-commands/blob/main/commands/{command}.md
```

## With Projects (Recommended)

1. Create a new Claude Project
2. In **Project Instructions**, paste contents of `project-instructions.md`
3. Optionally add the memory spec to guide memory updates

## Memory Integration

Claude.ai has built-in memory. When `/learn` identifies a standing preference:

1. Claude will suggest updating memory
2. Review the proposed change
3. Confirm to persist

Alternatively, manually edit in **Settings > Profile > Memories**.

## Verification

Test with:
```
/learn Always respond in bullet points for lists
```

Claude should acknowledge and offer to persist.
