# Example: Morning Briefing

This is what a typical session start looks like when the Bookend skill runs the morning briefing protocol.

---

## What the agent does

1. Reads `state/current.md`
2. Reads today's and yesterday's memory files
3. Reads `MEMORY.md` (long-term memory)
4. Presents a brief to the human

## Example output

> **Morning Briefing — 2026-02-15**
>
> **Where we left off:**
> You were working on the authentication refactor. The JWT middleware is done and tested. The session migration script is written but untested.
>
> **Top 3 priorities:**
>
> 1. Test and run the session migration script
> 2. Update API docs for the new auth endpoints
> 3. Review PR #47 (Maria's caching changes)
>
> **Open threads:**
>
> - Waiting on DevOps for staging env access (asked 2 days ago)
> - Design review for settings page scheduled for Thursday
>
> **From yesterday's memory:**
>
> - Decided to use RS256 instead of HS256 for JWT signing (better for microservices)
> - Found a bug in the rate limiter — fixed and deployed
>
> Ready to go. What would you like to tackle first?

---

## Key characteristics

- **Concise**: 30-second read, not a wall of text
- **Actionable**: Priorities are clear and ordered
- **Contextual**: References specific decisions and open threads
- **No repetition**: Doesn't re-explain things already captured in state
