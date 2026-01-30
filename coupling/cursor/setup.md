# Cursor Setup

Integrate learn commands into Cursor IDE.

## Quick Start (Project-Level)

1. Create `.cursorrules` in your project root
2. Add the contents of `cursorrules.md` from this directory

## Global Setup

1. Open Cursor Settings (Cmd/Ctrl + ,)
2. Go to **Features > Rules**
3. Add global rules from `cursorrules.md`

Or via file:

```bash
# Location varies by OS
# macOS: ~/Library/Application Support/Cursor/User/
# Linux: ~/.config/Cursor/User/
# Windows: %APPDATA%\Cursor\User\

cp cursorrules.md ~/.cursor/rules/learn-commands.md
```

## Storage Location

Cursor can persist learnings to:

```
your-project/
├── .cursorrules        # Project rules
├── .cursor/
│   └── learnings.md    # Stored learnings
└── ...
```

## With Cursor Composer

In Composer, you can invoke:
```
/learn Always prefer named exports over default exports
```

Cursor will acknowledge and can update .cursorrules directly.

## Verification

Open Composer and test:
```
/learn Use early returns to reduce nesting
```
