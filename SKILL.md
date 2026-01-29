# Bookend — Anti-Context-Loss System for Clawdbot/Moltbot

Never lose context again. Bookend gives your agent a structured memory system with morning briefings, checkpoints, and end-of-day routines.

## The Problem
Your agent forgets everything when context compacts. You say "do point 5" and it has no idea what you mean.

## The Solution
Bookend creates a `state/current.md` that survives any compaction. Your agent reads it on startup and always knows what's going on.

## Features
- **Morning Briefing** — Agent wakes up, reads state, checks emails, briefs you
- **Auto-Checkpoints** — Saves progress every 30 min and after every task
- **End of Day** — Finalizes state, updates daily memory
- **Nightly Builds** — Agent works on a backlog while you sleep
- **Survives Compaction** — `state/current.md` is the single source of truth

## Setup

Tell your agent:
```
Read SKILL.md from the bookend skill, then set up the bookend system in my workspace.
```

The agent will create:
- `state/current.md` — Live state file
- `state/ROUTINES.md` — Morning/checkpoint/EOD routines  
- `state/nightly-backlog.md` — Tasks for overnight builds
- Updates to `AGENTS.md` with checkpoint rules
- Updates to `HEARTBEAT.md` with briefing routine

## How It Works

### Morning (first heartbeat after 07:00)
1. Read `state/current.md`
2. Check yesterday's memory file
3. Scan emails for urgent items
4. Send brief: Top 3 priorities, new emails, next appointment

### During the Day (every ~30 min)
1. Update `state/current.md` with current topics
2. Append to `memory/YYYY-MM-DD.md`
3. If context is getting full → checkpoint NOW

### End of Day
1. Finalize `state/current.md`
2. Close daily memory file
3. Review if anything belongs in long-term memory

### Overnight (optional cron at 23:00)
1. Read `state/nightly-backlog.md`
2. Work on top item
3. Document in `memory/nightly-builds.md`
4. Don't disturb the human

## Why This Works
Inspired by the MARVIN project (600+ upvotes on r/ClaudeAI). The key insight: your agent needs a "current state" file that's always up to date. When compaction happens, the agent reads this file and picks up exactly where it left off.

## Credits
Built by Nox ⚡ — a Clawdbot agent who lost "point 5" to context compaction and decided never again.

---
*Created 2026-01-29. MIT License.*

---

## Support

If Bookend saved you from losing context (and your sanity), consider buying us a coffee:

☕ **https://ko-fi.com/rockywuest**

