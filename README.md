# Bookend

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![CI](https://github.com/rockywuest/bookend-skill/actions/workflows/ci.yml/badge.svg)](https://github.com/rockywuest/bookend-skill/actions/workflows/ci.yml)
[![Made for Claude Code](https://img.shields.io/badge/Made%20for-Claude%20Code-blue)](https://claude.ai/code)
[![Version](https://img.shields.io/badge/version-1.0.0-green)](https://github.com/rockywuest/bookend-skill/releases)

**Never lose context again. Structured memory system for AI assistants.**

---

## Quick Start

**1. Install the plugin**

```bash
# In Claude Code
/plugin install bookend
```

Or clone manually:

```bash
git clone https://github.com/rockywuest/bookend-skill.git ~/.claude/plugins/cache/bookend/latest
```

**2. Set up your workspace**

```
/setup
```

This creates `state/current.md`, `memory/`, `MEMORY.md`, and adds the bookend protocol to your `AGENTS.md`.

**3. Start using it**

Your agent will now automatically:
- Run a morning briefing at session start
- Checkpoint every ~30 minutes
- Wrap up at end of day

Say "checkpoint" anytime to trigger a manual save.

---

## The Problem

AI assistants forget. Session ends, context gone. Even within a session, context compaction loses details. After a week of "learning" your preferences, your assistant might:

- Present old news as new
- Forget decisions you already made
- Repeat mistakes you corrected
- Lose important context mid-conversation

## The Solution

**Bookend** implements a "bookend" pattern — structured check-ins at session start and end that capture state and ensure continuity.

```
Morning Briefing (Session Start)
├── Read state files → know where things stand
├── Check memory files → recall recent context
├── Scan for pending tasks → nothing falls through cracks
└── Brief the human → 30 second catch-up

Evening Wrap (Session End)
├── Capture today's events → daily memory file
├── Update state files → where things stand NOW
├── Flag open threads → what needs follow-up
└── Update long-term memory → lessons learned
```

Your assistant wakes up fresh each session, but these files ARE its memory. Structured files beat vague "remember this" instructions every time.

---

## How It Works

### Morning (session start)

1. Read `state/current.md`
2. Check yesterday's memory file
3. Scan for urgent items
4. Brief the human: top priorities, open threads, next steps

### During the Day (every ~30 min)

1. Update `state/current.md` with current topics
2. Append to `memory/YYYY-MM-DD.md`
3. If context is getting full — checkpoint NOW

### End of Day

1. Finalize `state/current.md`
2. Close daily memory file
3. Review if anything belongs in long-term memory

### Overnight (optional)

1. Read `state/nightly-backlog.md`
2. Work on top item from backlog
3. Document in `memory/nightly-builds.md`

---

## File Structure

```
your-workspace/
├── MEMORY.md           # Long-term memory (curated wisdom)
├── AGENTS.md           # Instructions (includes bookend protocol)
├── state/
│   └── current.md      # Right now: open threads, recent context
└── memory/
    ├── 2026-02-15.md   # Daily notes (raw events, decisions)
    ├── 2026-02-14.md
    └── ...
```

## Why It Works

- **Explicit state** — No "did we discuss this?" guessing
- **Daily files** — Easy to review, grep, reference
- **Curated memory** — Long-term file stays relevant (not just logs)
- **Checkpoint discipline** — Survive context compaction

---

## Installation Options

### Option A: Plugin Install (recommended)

```
/plugin install bookend
```

Then run `/setup` in your workspace.

### Option B: Manual Clone

```bash
git clone https://github.com/rockywuest/bookend-skill.git
```

Tell your agent: "Read SKILL.md from the bookend skill, then set up the bookend system in my workspace."

### Option C: Just the Protocol

Copy the snippet from [`templates/AGENTS-snippet.md`](templates/AGENTS-snippet.md) into your `AGENTS.md`. No plugin needed.

---

## Resources

| Directory | What's Inside |
|-----------|---------------|
| [`templates/`](templates/) | Starter files for your workspace (state, memory, AGENTS.md snippet) |
| [`examples/`](examples/) | Real-world examples of morning briefings, evening wraps, and filled state files |
| [`references/`](references/) | Patterns, anti-patterns, and best practices for using Bookend effectively |

---

## Integrations

Works with any AI assistant that can read/write files:

- [Claude Code](https://claude.ai/code) (native plugin support)
- [Clawdbot](https://github.com/clawdbot/clawdbot) / [Moltbot](https://moltbot.com)
- Claude Projects (with file upload)
- GPT with Code Interpreter
- Cursor, Codeium, Windsurf

## Origin

Built by **Nox** after experiencing 10+ memory failures in the first week of existence. The pattern is inspired by [MARVIN](https://github.com/livetheoogway/marvin-rules) and adapted for structured agent memory.

Lesson learned: **Memory is not optional. It's infrastructure.**

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to contribute. This project follows the [Contributor Covenant](https://www.contributor-covenant.org/version/2/1/code_of_conduct/) code of conduct.

## Security

See [SECURITY.md](SECURITY.md) for reporting vulnerabilities.

## License

[MIT](LICENSE)

---

[Support on Ko-fi](https://ko-fi.com/rockywuest)
