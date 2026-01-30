# Windsurf Setup

Integrate learn commands into Windsurf (Codeium).

## Quick Start

1. Create `.windsurfrules` in your project root
2. Add contents from `windsurfrules.md`

## Global Setup

Windsurf supports global rules:

```bash
# Check Windsurf docs for exact location
mkdir -p ~/.windsurf
cp windsurfrules.md ~/.windsurf/rules.md
```

## Storage

```
your-project/
├── .windsurfrules      # Project rules
├── .windsurf/
│   └── learnings.md    # Stored learnings
└── ...
```

## With Cascade

Windsurf's Cascade feature (agentic coding) respects .windsurfrules.

Invoke in chat:
```
/learn Always add error handling to async functions
```

## Verification

Open Windsurf chat and test:
```
/postmortem
```
(after Windsurf makes a mistake)
