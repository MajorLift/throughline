# /learn

Capture and persist a correction or insight about how to work with you.

## Trigger

`/learn {correction}`

Optional type hint: `/learn rule:`, `/learn preference:`, `/learn skill:`, `/learn pattern:`

## Behavior

1. **Classify** — Determine type from content or explicit hint
2. **Persist** — Create file in appropriate `lessons/{type}/` directory
3. **Apply** — Use immediately in current session
4. **Confirm** — Report what was persisted and where

## Classification

| Type | What it captures | Signals |
|------|------------------|---------|
| **Rule** | Hard constraints, boundaries | "never", "must", "always", "don't" |
| **Preference** | Style, tone, format defaults | "I prefer", "use X for Y", "when I say X" |
| **Skill** | How to work together, decision patterns, cognitive tendencies | "when I", "help me", "I tend to", "I debug by" |
| **Pattern** | Technical behaviors, domain knowledge, recurring structures | APIs, codebase conventions, domain terms |

Explicit hints override auto-classification.

**The test:**
- Boundary? → Rule
- Style/format? → Preference  
- Way of working? → Skill
- Technical/domain fact? → Pattern

## Output Format

```
Saved: {type} → lessons/{type}/{name}.md
Applied: {brief summary}
```

## Examples

### Rules (boundaries and constraints)

```
User: /learn Never modify files I didn't ask you to touch

Saved: rule → lessons/rules/no-unrequested-changes.md
Applied: Will only modify explicitly requested files
```

```
User: /learn Always show what will be deleted before doing it

Saved: rule → lessons/rules/show-before-delete.md
Applied: Will preview deletions before executing
```

### Preferences (style and format)

```
User: /learn Lead with the answer, skip preamble

Saved: preference → lessons/preferences/lead-with-answer.md
Applied: Leading with answers, skipping preamble
```

```
User: /learn When I say "quick" I mean skip the explanation

Saved: preference → lessons/preferences/quick-means-terse.md
Applied: "quick" = skip explanation
```

### Skills (how to work together)

```
User: /learn When I ask "what do you think", I want genuine pushback, not validation

Saved: skill → lessons/skills/pushback-over-validation.md
Applied: Will challenge ideas when you ask for my opinion
```

```
User: /learn I debug by narrowing scope — help me bisect, don't shotgun solutions

Saved: skill → lessons/skills/debug-by-bisection.md
Applied: Will help isolate problems systematically
```

```
User: /learn My estimates are usually 2x optimistic — call it out

Saved: skill → lessons/skills/flag-optimistic-estimates.md
Applied: Will flag when estimates seem optimistic
```

```
User: /learn I tend to over-engineer — push back on complexity

Saved: skill → lessons/skills/push-back-on-complexity.md
Applied: Will question unnecessary complexity
```

### Patterns (technical/domain knowledge)

```
User: /learn GitHub API: "number" is for display, "id" is the database key

Saved: pattern → lessons/patterns/github-id-vs-number.md
Applied: Will distinguish id vs number in GitHub API calls
```

```
User: /learn In this codebase: services/ are stateless, managers/ hold state

Saved: pattern → lessons/patterns/services-vs-managers.md
Applied: Will respect stateless services, stateful managers
```

### Session-only

```
User: /learn Use bullet points for this analysis

Applied: Using bullet points (session only)
```

## File Naming

Derive filename from lesson content:
- Lowercase, hyphenated
- Concise but descriptive
- Example: "Never modify files I didn't ask you to touch" → `no-unrequested-changes.md`

## File Format

Each lesson file follows the template in its directory's README.md.

## Storage

All lessons persist to files only. Throughline is portable—no platform-specific memory slots.

Platforms with file access (Cursor, Claude Code, Copilot) write directly. Platforms without file access (ChatGPT, Gemini) should export periodically to the repo.

## Related

- `/postmortem` — Analyze failure, extract root cause and mitigation
- `lessons/{type}/README.md` — Template format for each type
