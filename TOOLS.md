# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup: camera names and locations, SSH hosts and aliases, preferred TTS voices, speaker/room names, device nicknames, anything environment-specific.

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Local LLM (Ollama)

- **Base URL:** `http://localhost:11434/v1`
- **Default Model:** `gemma4:e4b`
- **API Key:** `ollama` (OpenAI-compatible)
- **Workflow Rule 1 (Universal Model Choice):** For **EVERY user request** (even simple one-line questions), **ALWAYS trigger a model selection prompt (ask_question)** first to let the user choose between **Local Model (Gemma 4:e4b)** and **Cloud Model (Gemini 3.7 Flash)**.
- **Workflow Rule 2 (Save Trigger):** Only save/create markdown files into category folders when user appends **`/저장해줘`** at the end of the prompt. Otherwise, just output the response in the chat without creating files.


## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

Add whatever helps you do your job. This is your cheat sheet.

## Related

- [Agent workspace](/concepts/agent-workspace)
