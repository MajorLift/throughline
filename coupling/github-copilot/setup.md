# GitHub Copilot Setup

Integrate learn commands into GitHub Copilot.

## Quick Start

1. Create `.github/copilot-instructions.md` in your repo root
2. Add contents from `copilot-instructions.md`

## How It Works

GitHub Copilot reads `.github/copilot-instructions.md` for repository-specific context. This works in:
- VS Code with Copilot Chat
- GitHub.com Copilot Chat
- JetBrains IDEs with Copilot

## Global Setup

For all repositories, you can:

1. Create a template repo with the instructions
2. Use GitHub's "Repository defaults" feature
3. Or add to each repo individually

## Storage

Copilot can write to files in your repo:

```
your-repo/
├── .github/
│   ├── copilot-instructions.md
│   └── learnings.md          # Stored learnings
└── ...
```

## Limitations

- Copilot doesn't have cross-session memory
- Learnings must be persisted to files
- Works best with Copilot Chat, not inline completions

## Verification

In Copilot Chat:
```
/learn Prefer async/await over .then() chains
```
