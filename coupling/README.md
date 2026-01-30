# Platform Configs

> **Quick start?** See the [README Platform Setup](../README.md#platform-setup) for the 4 most common platforms.
> 
> This directory contains configs for **all supported platforms**.

## Persistence Model

| Platform Type | How it persists | Setup |
|---------------|-----------------|-------|
| **IDE platforms** | Write directly to local filesystem | Point to local repo path |
| **Claude.ai + GitHub MCP** | Write via GitHub API | Point to GitHub repo URL |
| **Chat platforms (no MCP)** | Manual export | User copies lessons to repo |

---

## IDE Platforms (direct file access)

These platforms have filesystem access. Point them to your **local repo path**.

Replace `~/path/to/throughline` with your actual path (e.g., `~/repos/throughline` or `/Users/you/dev/throughline`).

### Cursor

> **Note:** Settings UI changed in v0.46. Instructions below are for v0.46+. For older versions, use General → Rules for AI instead of Rules → User Rules.

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

**Option B: Global settings**

1. Open Cursor Settings: `Cmd+Shift+J` (Mac) or `Ctrl+Shift+J` (Windows)
2. Navigate to **Rules** → **User Rules**
3. Paste the instructions (without YAML frontmatter)

### Claude Code

**File:** `~/.claude/CLAUDE.md` (global) or `CLAUDE.md` (project root)

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

### GitHub Copilot

**File:** `.github/copilot-instructions.md`

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

### Windsurf

**File:** `.windsurfrules`

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

### Continue.dev

**File:** `~/.continue/config.json`

```json
{
  "systemMessage": "My throughline repo is at ~/path/to/throughline. When /learn is used, classify as rule/preference/skill/pattern and create a file in lessons/{type}/. When /crystallize is used, scan conversation and propose a lesson for confirmation. When /postmortem is used, analyze failure, find root cause, suggest mitigation. On session start, read lessons/**/*.md."
}
```

### OpenCode

**File:** `AGENTS.md` or project config

```markdown
My throughline repo is at: ~/path/to/throughline

When I use /learn {something}:
- Classify as rule/preference/skill/pattern based on content
- Create a file in lessons/{type}/ with kebab-case filename
- Confirm: "Saved: {type} → lessons/{type}/{filename}.md"

When I use /crystallize:
- Scan conversation for patterns worth preserving
- Propose a lesson with type, summary, and filename
- Wait for my confirmation before saving

On session start, read lessons/**/*.md.
```

---

## Chat Platforms (no direct file access)

These platforms can't write to your filesystem directly.

### Claude.ai

**With GitHub MCP (enables persistence):**

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

Replace `{YOUR_USERNAME}` with your GitHub username.

**Without MCP (manual export):**

Same instructions, but lessons won't persist automatically. Periodically ask "list lessons from this session" and commit them to your repo manually.

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

**Export:** ChatGPT can't write to GitHub. Periodically ask "List all /learn lessons" and commit to your repo manually.

### Gemini

**Location:** System instructions (Gems or API)

```
When I use /learn {something}:
- Classify as rule/preference/skill/pattern
- Acknowledge the correction
- Apply immediately
- Note: Cannot persist across sessions without manual export

When I use /crystallize:
- Scan conversation for patterns worth preserving
- Propose a lesson with type, summary, and filename
- Wait for my confirmation

When I use /postmortem:
- What happened (facts)
- Root cause (not symptoms)
- Mitigation (concrete action)
- Pattern (generalizable insight)
```

**Export:** Ask "List all /learn lessons" and commit to your repo manually.

---

## Subdirectories

The `coupling/{platform}/` subdirectories contain additional platform-specific files (setup guides, example configs). Use these for advanced configuration.
