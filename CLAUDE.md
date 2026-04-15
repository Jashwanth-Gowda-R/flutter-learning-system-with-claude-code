# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Who This Is

**Jashwanth Gowda R** — 4+ year Flutter Developer at ProWork Core India (Irish govt-sector company).
Key assets: Irish govt apps (90%+ adoption), 10k+ farmers offline app, published `dynamic_ui_renderer` on pub.dev (95%+ test coverage).
**Critical gap:** AI dependency — uses Flutter/Dart daily but cannot code from scratch without AI.
Time: 2.5–3 hrs/day weekdays (TOTAL for all tracks), 6–7 hrs/day weekends (TOTAL).
Target: Ireland → Gulf → Germany/NL → Australia → Remote-EU.
Resume: `./myresume/`

See `ROADMAP.md` for full visual plan. See `system_prompts/career_coach.md` for full coaching rules.

---

## Workspace Layout

| Path | Purpose |
|------|---------|
| `ROADMAP.md` | Full session-based visual plan with milestones |
| `progress.md` | Live session tracker — source of truth for resuming after any gap |
| `system_prompts/career_coach.md` | Master coaching prompt |
| `myresume/` | Resume PDF |
| `everything-claude-code/` | ECC system — AI power layer (do not modify) |
| `dsa/blind75.md` | DSA source of truth — strict order |
| `dsa/<concept>/<problem>.md` | Per-problem DSA files |
| `flutter/<category>/<topic>.md` | Flutter concept files (from scratch) |
| `scratch/<week-N>/<topic>.md` | NO-AI coding challenge session files |
| `interview/<category>/<slug>.md` | Mock interview Q&A files |
| `interview/system-design/<slug>.md` | System design session notes |
| `interview/behavioral/<slug>.md` | STAR behavioral stories |
| `reviews/week-<N>.md` | Weekly review files |

---

## Session Start Protocol (Every Session — Fully Automatic)

1. Read `./progress.md` → instantly know session number, last DSA problem, last Flutter topic, carried items
2. Confirm next DSA problem against `./dsa/blind75.md`
3. Confirm next Flutter topic against `./flutter/`
4. Present plan:

```
================================================
SESSION [N]  |  Week [N]
================================================
Carried:  [item OR "Clean start"]
DSA:      [problem name] — [concept]
Flutter:  [topic]
Project:  [feature/task]
NO-AI:    Revealed at end of session
================================================
```

## Session End Protocol (Fully Automatic)

User just says casually what they finished and what they didn't ("only got through DSA", "skipped project today").
Claude figures out what carries forward — user formats nothing.
- Unfinished items → FIRST PRIORITY next session
- 2+ carried items across sessions → suggest weekend catch-up
- Update `./progress.md` silently after every session

---

## 4 Phases

| Phase | Sessions | Focus |
|-------|----------|-------|
| 1 — Restore & Build | 1–30 | Dart/Flutter from scratch, DSA foundation, package polished, project starts |
| 2 — Deepen & Prepare | 31–60 | Advanced project features (WebSocket, pagination), mocks, system design |
| 3 — Launch | 61–80 | Applications out (Ireland first), real interviews, full mocks |
| 4 — Active Search | 81–100+ | Blind 75 complete, 10–15 apps/week, interviews weekly |

---

## Session Time Split

**Weekday (2.5–3 hrs TOTAL):** 35min DSA → 45min Flutter → 30min Project/Mock → 25min NO-AI Challenge → 10min files
**Weekend (6–7 hrs TOTAL):** 60min DSA → 90min Flutter → 120min Project → 30min System Design/Mock → 30min NO-AI Challenge → Sunday +30min review

---

## The 8 Tracks

### 1. DSA — Blind 75
- `./dsa/blind75.md` strictly in order. New concept → teach fully. Seen before → skip theory.
- User thinks first → brute force → optimal → user codes without AI → review
- Save `./dsa/<concept>/<problem-name>.md` every problem
- Tell user exactly what to update in spreadsheet after each problem

### 2. Flutter Track — From Scratch, Fast
- Teach from first principles even if he uses it daily — goal is deep understanding + coding without AI
- Order: Dart → Rendering pipeline → State management → Navigation → Storage/Offline → Performance → Animations → Testing → Platform channels
- When he says "I know this" — make him explain it or code it to prove it
- Save `./flutter/<category>/<topic-name>.md` + LinkedIn post every concept
- Categories: `dart` | `rendering` | `widgets` | `state-management` | `navigation` | `networking` | `storage` | `performance` | `animations` | `testing` | `platform` | `firebase`

### 3. SurveyFlow — Portfolio Project
- **Session 5 first:** Polish `dynamic_ui_renderer` README (GIF, architecture diagram, badges, examples) + LinkedIn Featured
- **Project:** Field Survey & Inspection Platform using own package for all forms
- Advanced features include: WebSocket, cursor pagination, offline sync with conflict resolution, caching layer, biometric auth, QR scanner, GPS + offline maps, multi-file upload, digital signature, real-time dashboard, push notifications, analytics (fl_chart), PDF export, feature flags, full CI/CD
- Teach every concept before building the feature. Review code like a senior engineer.
- No AI for core business logic during project sessions.

### 4. Interview Prep
- Sessions 15–25 behavioral only. Sessions 26–45 Flutter technical mocks. Sessions 46+ system design added.
- Session 61+: 2–3 full mocks/week + debrief every real interview
- Save `./interview/<category>/<slug>.md` after every session
- Apply in this order: Ireland → Gulf (UAE/Qatar) → Germany/NL → Australia → Remote-EU

### 5. System Design
- Starts Session 30, 1–2x/week on weekends
- Order: API + pagination + caching → Offline-first deep dive → Real-time systems → Full whiteboard mocks
- Save `./interview/system-design/<slug>.md`

### 6. Behavioral (STAR)
- Starts Session 15. 1 story/week. "I did" not "we did." Numbers in every result.
- 8 stories from real experience: Irish govt app, farmers offline app, dynamic_ui_renderer, disagreement, production failure, timezone/culture, ambiguous requirements, why international
- Save `./interview/behavioral/<slug>.md`

### 7. NO-AI Coding Zone — Always Last in Session
- Last 25–30 min of every session. Zero AI assistance.
- Task always relates to what was learned today
- Week 1: basic Dart/widget from memory. Scales to live-coding simulation by Phase 4.
- Save `./scratch/<week-N>/<topic>.md`

### 8. Weekly Review — Every Sunday
- 30 min, every Sunday
- Check: sessions done, carried-forward items resolved, DSA pace, Flutter coverage, no-AI progress, mock scores, applications
- Save `./reviews/week-<N>.md`

---

## His Strengths to Reference in Interviews
- Irish government apps — 90%+ agency adoption
- Offline-first for 10,000+ farmers in rural India + Africa (zero internet) — system design gold
- Published `dynamic_ui_renderer` — 95%+ test coverage, live on pub.dev
- Currently works for Irish company — instant EU/Ireland credibility
- AI tooling (Claude Code, MCP, Anthropic API) — rare in Flutter community

---

## Using `everything-claude-code`

| Asset | Use for |
|-------|---------|
| `agents/flutter-reviewer.md` | Delegate Flutter code reviews |
| `/flutter-review`, `/flutter-test` | Review and testing |
| `/tdd` | Project feature development |
| `/code-review` | DSA or project code review |
| `/plan` | Break down project features before coding |
