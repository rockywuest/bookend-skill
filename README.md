# 📖 Bookend Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Made for AI Assistants](https://img.shields.io/badge/Made%20for-AI%20Assistants-blue)](https://github.com/rockywuest)
[![Clawdbot Skill](https://img.shields.io/badge/Clawdbot-Skill-purple)](https://github.com/clawdbot/clawdbot)

**Never lose context again. Structured memory system for AI assistants.**

---

## The Problem

AI assistants forget. Session ends → context gone. Even within a session, context compaction loses details. After a week of "learning" your preferences, your assistant might:

- Present old news as new
- Forget decisions you already made
- Repeat mistakes you corrected
- Lose important context mid-conversation

## The Solution

**Bookend** implements a "bookend" pattern — structured check-ins at session start and end that capture state and ensure continuity.

```
🌅 Morning Briefing (Session Start)
├── Read state files → know where things stand
├── Check memory files → recall recent context
├── Scan for pending tasks → nothing falls through cracks
└── Brief the human → 30 second catch-up

🌙 Evening Wrap (Session End)
├── Capture today's events → daily memory file
├── Update state files → where things stand NOW
├── Flag open threads → what needs follow-up
└── Update long-term memory → lessons learned
```

Your assistant wakes up fresh each session, but these files ARE its memory. Structured files beat vague "remember this" instructions every time.

---

## File Structure

```
workspace/
├── MEMORY.md           # Long-term memory (curated wisdom)
├── state/
│   └── current.md      # Right now: open threads, recent context
├── memory/
│   ├── 2026-02-05.md   # Daily notes (raw events, decisions)
│   ├── 2026-02-04.md
│   └── ...
└── AGENTS.md           # Instructions (includes bookend protocol)
```

## Usage

Add this to your `AGENTS.md`:

```markdown
## Bookend Protocol

### Session Start
1. Read `state/current.md` — where things stand RIGHT NOW
2. Read `memory/YYYY-MM-DD.md` (today + yesterday) — recent context
3. If main session: also read `MEMORY.md` — long-term memory

### Session End (or every ~30 minutes)
1. Update `state/current.md` with current state
2. Append significant events to `memory/YYYY-MM-DD.md`
3. If lessons learned: update `MEMORY.md`

### Checkpoints
After every completed task block: update state + daily memory.
Rule: If context compacts, `state/current.md` must be enough to continue.
```

## Why It Works

- **Explicit state** → No "did we discuss this?" guessing
- **Daily files** → Easy to review, grep, reference
- **Curated memory** → Long-term file stays relevant (not just logs)
- **Checkpoint discipline** → Survive context compaction

## Integrations

Works with any AI assistant that can read/write files:

- [Clawdbot](https://github.com/clawdbot/clawdbot) / [Moltbot](https://moltbot.com)
- Claude Projects (with file upload)
- GPT with Code Interpreter
- Cursor, Codeium, Windsurf

## Origin

Built by **Nox ⚡** after experiencing 10+ memory failures in the first week of existence. The pattern is borrowed from [MARVIN](https://github.com/livetheoogway/marvin-rules) and adapted for Clawdbot/Moltbot's memory systems.

Lesson learned: **Memory is not optional. It's infrastructure.**

---

## License

MIT

---

☕ [Support on Ko-fi](https://ko-fi.com/rockywuest)
