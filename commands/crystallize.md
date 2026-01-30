# /crystallize

Extract a reusable lesson from the current conversation.

## Trigger

`/crystallize` or `/crystallize {hint}`

## Aliases

`/crys`

## Purpose

When a conversation reveals something worth preserving — a pattern, a correction, a preference — extract it as a lesson without the user having to articulate it themselves.

Unlike `/learn` where user states the lesson directly, `/crystallize` asks the AI to identify and propose what's worth saving.

## When to Use

- After a productive debugging session
- When a correction reveals a deeper pattern
- After several back-and-forth iterations that refined an approach
- When user says "that's useful" or "I'll remember that"

## Procedure

```
1. SCAN CONVERSATION
   Look for:
   - Corrections user made ("no, I meant...")
   - Preferences revealed ("I prefer...", "don't...")
   - Patterns that emerged through iteration
   - Techniques that worked well
   - Mistakes that should be avoided

2. PROPOSE LESSON
   Present candidate lesson:
   - One sentence summary
   - Suggested type (rule/preference/skill/pattern)
   - Suggested filename

3. CONFIRM
   Wait for user approval or edits

4. SAVE
   Create file in lessons/{type}/{filename}.md
   Use format from lessons/{type}/README.md

5. REPORT
   "Saved: {type} → lessons/{type}/{filename}.md"
```

## Output Format

```
## Proposed Lesson

**Type:** skill
**Summary:** When debugging, bisect the problem space rather than shotgunning solutions
**Filename:** debug-by-bisection.md

Save this? [Y/n/edit]
```

After confirmation:

```
Saved: skill → lessons/skills/debug-by-bisection.md
```

## Examples

### After Debugging Session

```
[conversation where user kept narrowing down a bug methodically]

User: /crystallize

AI: ## Proposed Lesson

    **Type:** skill  
    **Summary:** When debugging, narrow scope systematically — bisect rather than shotgun
    **Filename:** debug-by-bisection.md

    Save this? [Y/n/edit]

User: y

AI: Saved: skill → lessons/skills/debug-by-bisection.md
```

### After Repeated Correction

```
[user corrected AI's verbose responses multiple times]

User: /crystallize

AI: ## Proposed Lesson

    **Type:** preference
    **Summary:** Lead with the answer, skip preamble and caveats unless asked
    **Filename:** lead-with-answer.md

    Save this? [Y/n/edit]

User: edit: "Lead with answer. No 'Sure!' or 'Great question!'"

AI: ## Updated Lesson

    **Type:** preference
    **Summary:** Lead with answer. No 'Sure!' or 'Great question!'
    **Filename:** lead-with-answer.md

    Save this? [Y/n/edit]

User: y

AI: Saved: preference → lessons/preferences/lead-with-answer.md
```

### Nothing Worth Crystallizing

```
User: /crystallize

AI: I don't see a clear lesson from this conversation worth preserving. 
    We discussed [topic] but nothing emerged that would generalize.
    
    Is there something specific you'd like to save?
```

## Lesson Types

| Type | What it captures | Signals |
|------|------------------|---------|
| **rule** | Hard constraints | "never", "always", "don't" |
| **preference** | Style/format defaults | "I prefer", "I like", tone feedback |
| **skill** | How to work together | Collaboration patterns, decision approaches |
| **pattern** | Technical/domain knowledge | API behaviors, codebase conventions |

## Anti-Patterns

| Bad | Good |
|-----|------|
| Crystallizing trivial exchanges | Only meaningful patterns |
| Saving without confirmation | Always confirm first |
| Overly specific lessons | Generalize appropriately |
| Multiple lessons at once | One at a time |

## Related

- `/learn {lesson}` — User states lesson directly
- `/postmortem` — Extract lesson from failure specifically
