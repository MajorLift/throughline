# OpenCode Setup

Integrate learn commands into OpenCode.

## Quick Start

1. Locate OpenCode configuration
2. Add system instructions from `instructions.md`

## Project-Level Configuration

```
your-project/
├── .opencode/
│   ├── config.yaml      # Or relevant config
│   └── learnings.md     # Stored learnings
└── ...
```

## Configuration Options

Depending on OpenCode version, add to:
- Global settings
- Project config file
- Per-session instructions

```yaml
assistant:
  instructions: |
    Support /learn and /postmortem commands.
    See instructions.md for full specification.
```

## Storage

OpenCode can persist learnings to:
- Local files (recommended)
- Project-specific locations
- Global learnings directory

## Verification

```
/learn Use type hints for all function signatures
```
