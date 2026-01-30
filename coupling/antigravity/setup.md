# Antigravity Setup

Integrate learn commands into Antigravity.

## Quick Start

1. Open Antigravity settings
2. Navigate to AI/Assistant configuration
3. Add system instructions from `instructions.md`

## Project-Level

If Antigravity supports project-level config:

```
your-project/
├── .antigravity/
│   ├── config.yaml      # Or relevant config file
│   └── learnings.md     # Stored learnings
└── ...
```

## Configuration

Add to your Antigravity AI settings:

```yaml
ai:
  system_instructions: |
    When user invokes /learn, acknowledge and apply corrections.
    When user invokes /postmortem, analyze failures with root cause and mitigation.
```

See `instructions.md` for full instructions.

## Verification

```
/learn Always validate inputs before processing
```
