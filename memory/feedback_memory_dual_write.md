---
name: Dual memory write — both locations
description: Always write memories to both ~/.claude/.../memory/ AND ./memory/ in the repo
type: feedback
---

When saving any memory, always write to both:
1. `~/.claude/projects/-Users-jashwanthgowda-personal-flutter-abroad-system/memory/` — local Claude memory
2. `./memory/` in the repo (`/Users/jashwanthgowda/personal/flutter-abroad-system/memory/`) — git-tracked backup

Also update MEMORY.md index in both locations.

**Why:** Local ~/.claude/ is lost if machine changes. Repo memory is committed to git and survives anywhere.

**How to apply:** Every single memory write — no exceptions. Both files, both indexes.
