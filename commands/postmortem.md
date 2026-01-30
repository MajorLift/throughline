# /postmortem

Analyze failure, extract root cause, and specify preventive mitigation.

## Trigger

`/postmortem` or `/postmortem {what went wrong}`

## Aliases

`/rca`, `/retro`

## Purpose

When something fails or requires multiple attempts, extract the **generalizable pattern** that would have prevented it. Not about compliance or blame—about systematic improvement.

## Critical Requirement: Mitigations

**Every postmortem MUST include concrete mitigation.** Identifying problems without fixes is just confession.

| Acceptable | Not Acceptable |
|------------|----------------|
| "Add checklist: verify X before Y" | "I'll do better next time" |
| "Update spec to require Z" | "This response uses proper formatting" |
| "No structural fix—manual discipline" | Silent omission of mitigation |

If no systematic prevention is possible, say so explicitly.

## When to Use

- After repeated failures on a task
- When user corrects a mistake
- After discovering a tool/API misunderstanding
- When a process took much longer than expected

## Procedure

```
1. IDENTIFY THE FAILURE
   - What was attempted?
   - What went wrong?
   - How many attempts before success?

2. FIND ROOT CAUSE (not symptoms)
   - Why did the first attempt fail?
   - What assumption was wrong?
   - What knowledge was missing?

3. SPECIFY MITIGATION (REQUIRED)
   - Structural: spec update, checklist, validation rule
   - Procedural: new step in existing workflow
   - Detection: how to catch this earlier
   - If impossible: "No structural fix—manual discipline"

4. EXTRACT PATTERN (generalized)
   - What class of problems does this represent?
   - Frame as: "When X, always Y before Z"

5. PRESENT TO USER FOR VALIDATION
   - Root cause analysis involves interpretation
   - User may have better insight into actual cause

6. PERSIST (after approval)
   - Write to appropriate learnings file
   - Brief: trigger → mitigation → why
```

## Output Format

```
**Failure:** [what went wrong]
**Root cause:** [actual why, not symptoms]
**Mitigation:** [concrete prevention—REQUIRED]
**Pattern:** When [trigger], always [action]

Proceed with persisting? [Y/n]
```

After confirmation:

```
Applied: [brief summary]
Location: [file path]
```

## Examples

### API Misunderstanding

```
User: /postmortem

AI: **Failure:** API call failed 4 times with 404
    **Root cause:** Used item NUMBER instead of item ID
    **Mitigation:** Add to learnings: "When API params say 'id', 
      verify whether it means database ID or display number"
    **Pattern:** When using IDs, check ID type before calling

    Proceed with persisting? [Y/n]

User: y

AI: Applied: API ID vs number distinction
    Location: learnings/api-patterns.md
```

### Process Gap

```
User: /postmortem violated constraint

AI: **Failure:** Violated user constraint "not in current directory"
    **Root cause:** Parsed task requirements but not constraints
    **Mitigation:** "Extract constraints (negatives, boundaries) 
      as first parsing step"
    **Pattern:** When receiving instructions, extract constraints
      before planning actions

    Proceed with persisting? [Y/n]
```

### No Structural Fix

```
User: /postmortem typo in response

AI: **Failure:** Misspelled "accommodation"
    **Root cause:** Token-level generation, no spell-check layer
    **Mitigation:** No structural fix available—manual proofreading 
      on high-stakes outputs
    **Pattern:** N/A (inherent to generation process)

    Proceed with persisting? [Y/n]
```

## Anti-Patterns

| Bad | Good |
|-----|------|
| "I apologize for the confusion" | Skip—focus on pattern |
| "I'll be more careful" | Concrete structural change |
| Listing 5 symptoms | Find 1 root cause |
| Persisting without validation | Confirm conclusions first |
| Omitting mitigation | ALWAYS include prevention |

## Key Principles

1. **Root causes** — Multiple failures usually share ~1 common cause
2. **Mitigation required** — No fix = say so explicitly
3. **Generalize aggressively** — "Check ID type" not "API X uses database ID"
4. **Actionable trigger** — Pattern must say WHEN to apply it
5. **No apologies** — Postmortems are engineering, not customer service
6. **Validate before persisting** — User may have better insight

## Related

- `/learn` — Apply single correction immediately (no failure needed)