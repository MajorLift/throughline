# Claude Code Setup

Integrate learn commands into Claude Code CLI.

## Quick Start

1. Create or edit `CLAUDE.md` in your project root
2. Add the contents of `CLAUDE.md` from this directory

## Global Setup

For learn commands in all projects:

```bash
# Create global config directory
mkdir -p ~/.claude

# Add global instructions
cat >> ~/.claude/CLAUDE.md << 'EOF'
# Learn Commands

When user invokes /learn or /postmortem, execute according to:
https://github.com/MajorLift/learn-commands/blob/main/commands/{command}.md
EOF
```

## Storage Location

Claude Code can write learnings directly to files:

```
your-project/
├── CLAUDE.md           # Project instructions
├── .claude/
│   └── learnings.md    # Stored learnings
└── ...
```

Add to CLAUDE.md:
```
Store learnings in .claude/learnings.md
```

## Verification

```bash
claude
> /learn Always use descriptive variable names
```

Should acknowledge and optionally persist to learnings file.
