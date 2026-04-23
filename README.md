# Flutter Abroad Learning System

A structured, session-based personal learning system built to take a senior Flutter developer from AI-dependent to fully interview-ready — targeting senior Flutter roles in Ireland, UAE/Qatar, Germany/Netherlands, Australia, and Remote-EU.

---

## What This Is

Not a course. Not a tutorial list. A **personal operating system** for deliberate practice across 8 tracks, running in parallel, tracked session by session.

Built for: **Jashwanth Gowda R** — 4+ years Flutter, Irish govt-sector company, published [dynamic_ui_renderer](https://pub.dev/packages/dynamic_ui_renderer) on pub.dev.

Core problem this solves: deep Flutter experience but AI-dependent for coding from scratch. Goal is to restore raw ability, build first-principles understanding, and become ready for senior-level global interviews.

---

## The 4 Phases

| Phase | Sessions | Focus |
|-------|----------|-------|
| 1 — Restore & Build | 1–30 | Dart/Flutter from scratch, DSA foundation, package polished |
| 2 — Deepen & Prepare | 31–60 | Advanced project features, mock interviews, system design |
| 3 — Launch | 61–80 | Applications out (Ireland first), real interviews, full mocks |
| 4 — Active Search | 81–100+ | Blind 75 complete, 10–15 apps/week, interviews weekly |

---

## The 8 Tracks

| Track | What |
|-------|------|
| DSA | Blind 75 — strict order, no skipping |
| Flutter | Dart → Rendering → State → Navigation → Storage → Performance → Animations → Testing → Platform |
| SurveyFlow Project | Field Survey & Inspection Platform — portfolio-grade production app |
| Interview Prep | Flutter technical, system design, behavioral STAR stories |
| System Design | Starts Session 30 — offline-first, real-time, API design |
| Behavioral (STAR) | 8 core stories from real experience |
| NO-AI Coding Zone | Last 25–30 min every session — zero AI, zero autocomplete |
| Weekly Review | Every Sunday — track progress, catch carry-forwards |

---

## Workspace Layout

```
flutter-abroad-system/
│
├── progress.md                          Live session tracker — source of truth
├── start.txt                            Paste this to resume the next session
├── ROADMAP.md                           Full visual plan with milestones
├── CLAUDE.md                            Instructions for Claude Code
│
├── system_prompts/
│   └── career_coach.md                  Master coaching prompt
│
├── dsa/
│   ├── blind75.md                       Problem list — strict top-to-bottom order
│   └── <concept>/
│       └── <problem>.md                 Per-problem notes (intuition, code, complexity)
│
├── flutter/                             Flutter learning — organised by category
│   ├── dart/                            Dart language topics
│   ├── rendering/                       Widget/Element/RenderObject trees (Phase B)
│   ├── widgets/
│   ├── state-management/                Riverpod, InheritedWidget, setState
│   ├── navigation/                      GoRouter, Navigator
│   ├── networking/                      Dio, Repository pattern
│   ├── storage/                         Hive, Drift, offline-first
│   ├── performance/
│   ├── animations/
│   ├── testing/
│   ├── platform/
│   └── firebase/
│
├── no-ai/
│   └── week-<N>/
│       └── <topic>.md                   NO-AI coding challenge files (zero AI, every session)
│
├── interview/                           Created at Session 15
│   ├── flutter-technical/
│   ├── dart-language/
│   ├── architecture/
│   ├── system-design/
│   ├── behavioral/
│   └── dsa-applied/
│
├── reviews/
│   └── week-<N>.md                      Weekly Sunday reviews (starts Week 1)
│
├── projects/
│   └── production_app/                  SurveyFlow Flutter project (built from Session 15)
│
├── memory/                              Claude behavioral preferences — git-tracked
│   └── MEMORY.md                        Index of all memory files
│
├── myresume/                            Resume PDF
├── career/                              career-ops submodule (active from Session 61)
└── everything-claude-code/              ECC AI power layer — do not modify
```

---

## Session Structure

**Weekday (2.5–3 hrs total)**
```
35 min   DSA — concept + solve + code without AI
45 min   Flutter — teach → understand → code key parts
30 min   Project feature or mock interview
25 min   NO-AI Coding Challenge  ← always last
10 min   Save files + report done/not-done
```

**Weekend (6–7 hrs total)**
```
60 min   DSA — 2 problems or 1 hard with deep review
90 min   Flutter — deep dive + build something real
120 min  Project — main feature build window
30 min   System design or full mock interview
30 min   NO-AI Coding Challenge  ← always last
+30 min  Weekly Review (Sunday only)
```

---

## Key Milestones

| Session | Milestone |
|---------|-----------|
| 5 | dynamic_ui_renderer README polished + LinkedIn Featured |
| 15 | SurveyFlow repo live, Clean Architecture structure done |
| 25 | Auth + Dynamic forms + QR scanner working |
| 60 | Resume final, LinkedIn polished, GitHub clean — ready to apply |
| 61 | First job application sent |
| 95 | Blind 75 complete |
| 100 | Offer stage |

---

## Non-Negotiables

1. NO-AI zone — every session, last 25–30 min, zero exceptions
2. DSA — blind75.md order, never skip
3. Partial completion — always report done/not-done at session end
4. Weekly review — every Sunday
5. Every mock or real interview → saved to file → debriefed
6. Applications never stop once Phase 3 starts

---

## How Sessions Work

Sessions are tracked, not calendar days. Miss a day — resume next session, no catch-up doubling, no guilt. Timeline extends naturally.

At session end, just say what got done and what didn't. Unfinished items carry forward automatically as first priority next session.

Current state: `progress.md`
Full plan: `ROADMAP.md`
Coaching rules: `system_prompts/career_coach.md`
