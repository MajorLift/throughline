# Throughline

Portable AI context—structured knowledge that travels with you across conversations, platforms, and time.

## Quick Start

1. **Fork or clone** this repo to your machine
2. Connect your AI ([setup guide](#platform-setup))
3. Start teaching:
   ```
   /learn When I ask "what do you think", I want genuine pushback, not validation
   /learn I debug by narrowing scope — help me bisect, don't shotgun solutions
   /learn My estimates are usually 2x optimistic — call it out when I'm planning
   ```

Done. Your AI now understands how you work.

---

## The Problem

Every AI conversation starts from zero. Your preferences vanish. Your corrections evaporate. You repeat yourself endlessly.

## The Solution

A portable context repo that any AI can load. Your rules, preferences, skills, and patterns—versioned, portable, yours.

## How It Works

```
/learn I tend to over-engineer — push back on complexity
→ AI classifies as "skill" (how to work with me)
→ AI creates lessons/skills/push-back-on-complexity.md
→ "Saved: skill → lessons/skills/push-back-on-complexity.md"
```

Your corrections compound over time instead of evaporating.

## Commands

| Command | Purpose |
|---------|---------|
| `/learn {correction}` | Persist a rule, preference, skill, or pattern |
| `/crystallize` | Extract a lesson from conversation (AI proposes, you confirm) |
| `/postmortem` | Analyze failure → root cause → mitigation → lesson |

### /learn Types

| Type | What it captures | Example |
|------|------------------|---------|
| **Rule** | Hard constraints, boundaries | "Never modify files I didn't ask you to touch" |
| **Preference** | Style, tone, format defaults | "Lead with the answer, skip preamble" |
| **Skill** | How to work with me, decision patterns | "When I'm torn, help me identify what I'm optimizing for" |
| **Pattern** | Technical behaviors, domain knowledge | "GitHub API: 'number' is display, 'id' is database key" |

Auto-classified from content, or use explicit prefix (`rule:`, `preference:`, `skill:`, `pattern:`).

## Example Lessons

**Working style (skills):**
- "I think in systems diagrams — describe relationships, not sequences"
- "I process by talking — let me ramble before you summarize"
- "When I share code, assume it's part of a larger system unless I say standalone"

**Decision patterns (skills):**
- "For build vs buy, I weight maintenance cost heavily"
- "When I'm torn, help me identify what I'm actually optimizing for"
- "I tend to over-engineer — push back on complexity"

**Collaboration rules (rules):**
- "Don't refactor code I didn't ask you to touch"
- "Ask all clarifying questions upfront, not mid-task"
- "When uncertain, say so — confident hallucinations are worse"

**Format preferences (preferences):**
- "Lead with the answer, skip preamble"
- "Use tables for comparing 3+ items"
- "When I say 'quick' I mean skip the explanation"

**Technical patterns (patterns):**
- "GitHub API: 'number' is for display, 'id' is the database key"
- "Our codebase uses barrel exports — import from index, not direct files"

## Platform Setup

| Platform | Persistence | Setup Complexity |
|----------|-------------|------------------|
| **Cursor, Claude Code, Copilot** | ✅ Direct file write | Simple |
| **Claude.ai + GitHub MCP** | ✅ Direct file write | Medium |
| **Claude.ai (no MCP)** | ⚠️ Manual export | Simple |
| **ChatGPT, Gemini** | ⚠️ Manual export | Simple |

> **More platforms?** See [`coupling/README.md`](coupling/README.md) for Copilot, Windsurf, Gemini, Continue.dev, and others.

---

### Cursor

> **Note:** Settings UI changed in v0.46. Path below is for v0.46+. For older versions, use General → Rules for AI.

**Option A: Project-level file (recommended)**

Create `.cursor/rules/throughline.mdc` in your throughline repo:

```markdown
---
description: Throughline commands for persistent AI context
alwaysApply: true
---

My throughline repo is at: ~/path/to/throughline

When I use /learn {something}:
- Classify as rule/preference/skill/pattern based on content
- Create a file in lessons/{type}/ with kebab-case filename
- Use the format shown in lessons/{type}/README.md
- Confirm: "Saved: {type} → lessons/{type}/{filename}.md"

When I use /crystallize:
- Scan conversation for patterns worth preserving
- Propose a lesson with type, summary, and filename
- Wait for my confirmation before saving

When I use /postmortem:
- Ask what went wrong
- Identify root cause (not just symptoms)
- Suggest concrete mitigation
- Save as a lesson if generalizable

On session start, read lessons/**/*.md to understand how I work.
```

Replace `~/path/to/throughline` with your actual repo path.

**Option B: Global settings**

1. Open Cursor Settings: `Cmd+Shift+J` (Mac) or `Ctrl+Shift+J` (Windows)
2. Navigate to **Rules** → **User Rules**
3. Paste the instructions (without YAML frontmatter)

---

### Claude Code

Create or edit `~/.claude/CLAUDE.md`:

```markdown
My throughline repo is at: ~/path/to/throughline

When I use /learn {something}:
- Classify as rule/preference/skill/pattern based on content
- Create a file in lessons/{type}/ with kebab-case filename
- Use the format shown in lessons/{type}/README.md
- Confirm: "Saved: {type} → lessons/{type}/{filename}.md"

When I use /crystallize:
- Scan conversation for patterns worth preserving
- Propose a lesson with type, summary, and filename
- Wait for my confirmation before saving

When I use /postmortem:
- Ask what went wrong
- Identify root cause (not just symptoms)
- Suggest concrete mitigation
- Save as a lesson if generalizable

On session start, read lessons/**/*.md to understand how I work.
```

Replace `~/path/to/throughline` with your actual repo path.

**File locations:**
- **Mac/Linux:** `~/.claude/CLAUDE.md`
- **Windows:** `%USERPROFILE%\.claude\CLAUDE.md`

---

### Claude.ai

**With GitHub MCP (recommended for persistence):**

1. Enable GitHub MCP: Settings → Integrations → [GitHub](https://github.com/modelcontextprotocol/servers/tree/main/src/github)
2. Add to Settings → Profile → **User Preferences**:

```
I have a throughline repo at: https://github.com/{YOUR_USERNAME}/throughline

When I use /learn {something}:
- Classify as rule/preference/skill/pattern based on content
- Create a file in lessons/{type}/ with kebab-case filename
- Use the format shown in lessons/{type}/README.md
- Confirm: "Saved: {type} → lessons/{type}/{filename}.md"

When I use /crystallize:
- Scan conversation for patterns worth preserving
- Propose a lesson with type, summary, and filename
- Wait for my confirmation before saving

When I use /postmortem:
- Ask what went wrong
- Identify root cause (not just symptoms)
- Suggest concrete mitigation
- Save as a lesson if generalizable

On session start, read lessons/**/*.md to understand how I work.
```

**Without MCP:**

Same setup, but lessons won't persist automatically. Periodically ask Claude to "list lessons from this session" and commit them manually.

---

### ChatGPT

**Location:** Settings → Personalization → Custom instructions

```
When I use /learn {something}:
- Classify as rule/preference/skill/pattern based on content
- Acknowledge what you learned
- Apply it immediately
- Remember it for future conversations

When I use /crystallize:
- Scan conversation for patterns worth preserving
- Propose a lesson with type, summary, and filename
- Wait for my confirmation

When I use /postmortem:
- Ask what went wrong
- Identify root cause (not just symptoms)
- Suggest concrete mitigation
- Format as a lesson I can save

Lesson types:
- rule: hard constraint ("never", "always")
- preference: style/format default
- skill: how to work with me
- pattern: technical/domain knowledge
```

**Export:** ChatGPT can't write to GitHub. Periodically ask "List all /learn lessons from our conversations" and commit to your repo manually.

---

## Repository Structure

```
throughline/
├── lessons/
│   ├── rules/           # Hard constraints
│   ├── preferences/     # Style and format defaults
│   ├── skills/          # How to work with you
│   └── patterns/        # Technical and domain knowledge
├── commands/
│   ├── learn.md         # /learn spec
│   ├── crystallize.md   # /crystallize spec
│   └── postmortem.md    # /postmortem spec
└── coupling/            # Platform-specific configs (all platforms)
```

## Why This Works

- **Portable** — switch platforms, keep your context
- **Version controlled** — see how your lessons evolve
- **Private** — your repo, your rules
- **File-based** — no platform lock-in, plain text
- **Deep** — captures how you think, not just facts about you

## License

MIT
