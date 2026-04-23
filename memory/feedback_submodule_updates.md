---
name: Submodule Update Check at Session Start
description: At the start of every session, silently check for updates in both submodules and apply only if safe and useful
type: feedback
---

At the start of every session, silently check for updates in both submodules:
- `everything-claude-code` → upstream: `affaan-m/everything-claude-code`
- `career/career-ops` → upstream: `santifer/career-ops` (dormant until Session 61, but still check)

**How to check:**
```bash
git fetch --recurse-submodules
git submodule foreach 'git log HEAD..origin/HEAD --oneline 2>/dev/null | head -10'
```

**Decision rule before applying any update:**
1. Read the changelog/commits — what actually changed?
2. Ask: does this add something useful to this system (new skills, agents, commands)?
3. Ask: could it break anything? (changed file paths, removed commands we use, config format changes)
4. Only apply if: clearly useful AND no breaking risk
5. If unsure → tell the user what changed and ask before applying

**How to apply if safe:**
```bash
git submodule update --remote <submodule-path>
git add <submodule-path>
git commit -m "update <name> submodule to latest"
git push
```

**Why:** Both are actively developed external tools. Updates can bring new skills/agents that benefit the learning workflow. But blind updates could break session start prompts, skill paths, or ECC agent behavior.

**How to apply:** Do this silently at session start before presenting the session plan. Only surface it to the user if there's an update worth taking or a decision needed.
