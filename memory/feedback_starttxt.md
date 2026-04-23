---
name: Update start.txt at session end
description: Always update start.txt at the end of every session with the next session's resume prompt
type: feedback
---

At the end of every session, always update `start.txt` with the next session's context — session number, what's done, what's next for DSA/Flutter/Project/NO-AI.

**Why:** User pastes start.txt as the opening message to resume the session in a new Claude conversation. If it's stale, the next session starts with wrong context.

**How to apply:** Part of session-end protocol, same as updating progress.md. Do both together, every session without exception.
