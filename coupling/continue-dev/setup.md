# Continue.dev Setup

Integrate learn commands into Continue (VS Code / JetBrains).

## Quick Start

1. Open Continue settings (gear icon in Continue panel)
2. Edit `config.json`
3. Add system message from `config-snippet.json`

## Config Location

```
~/.continue/config.json
```

## Configuration

Add to your `config.json`:

```json
{
  "models": [...],
  "systemMessage": "When user invokes /learn, acknowledge and apply the correction. Classify as session-only, standing preference, or skill. When user invokes /postmortem, analyze: what happened, root cause, mitigation (required), pattern."
}
```

Or use the full version in `config-snippet.json`.

## Storage

Continue can write to files:

```
your-project/
├── .continue/
│   ├── config.json
│   └── learnings.md    # Stored learnings
└── ...
```

## Verification

In Continue chat:
```
/learn Prefer composition over inheritance
```
