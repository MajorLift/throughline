# Gemini Setup

Integrate learn commands into Google Gemini.

## Quick Start (Gemini Advanced)

1. Open Gemini and go to **Settings**
2. Find **Extensions** or **Gems** (varies by version)
3. Create a custom Gem with instructions from `system-instructions.md`

## For Google AI Studio

1. Open [AI Studio](https://aistudio.google.com)
2. Create new prompt or tune
3. In System Instructions, paste contents of `system-instructions.md`

## For Vertex AI

Add to your system prompt in API calls:

```python
model = genai.GenerativeModel(
    model_name="gemini-pro",
    system_instruction=open("system-instructions.md").read()
)
```

## Limitations

- Gemini doesn't have persistent memory like Claude
- Learnings must be manually tracked or re-added each session
- Consider using a Google Doc as external storage

## Verification

```
/learn Always provide code examples with explanations
```
