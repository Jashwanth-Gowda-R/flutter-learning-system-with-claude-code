# Abroad Job Roadmap — Jashwanth Gowda R

**Not a beginner program.** Skill restoration + depth + global senior Flutter role.
**Tracking:** Sessions, not calendar days. Partial sessions carry forward. Timeline extends as needed.

---

## The Big Picture

```
SESSION 1──────────────SESSION 30──────────────SESSION 60──────────────SESSION 95+
     │                       │                       │                      │
  PHASE 1                PHASE 2                PHASE 3                PHASE 4
  RESTORE                DEEPEN                 LAUNCH                 GRIND
  ─────────              ───────                ──────                 ─────
  Dart from scratch      Project grows          Apply: Ireland first   Blind 75 done
  Flutter from scratch   Mocks start            Gulf + EU + AUS        3 interviews/week
  DSA foundation         System design          GitHub polished        Never stop learning
  Package polished       WebSocket, pagination  Real interviews begin  Offer incoming
```

---

## Time Per Session

```
WEEKDAY (2.5–3 hrs TOTAL)
  ┌─────────────────────────────────────────────────┐
  │ 35 min  DSA (concept + solve + code)            │
  │ 45 min  Flutter (teach → understand → code)     │
  │ 30 min  Project feature or mock interview       │
  │ 25 min  NO-AI Coding Challenge ← always LAST    │
  │ 10 min  Save files + report done/not-done       │
  └─────────────────────────────────────────────────┘

WEEKEND (6–7 hrs TOTAL)
  ┌─────────────────────────────────────────────────┐
  │ 60 min  DSA (2 problems or 1 hard + review)     │
  │ 90 min  Flutter deep dive (build something)     │
  │ 120 min Project feature (main build window)     │
  │ 30 min  System design or full mock interview    │
  │ 30 min  NO-AI Coding Challenge ← always LAST    │
  │ +30 min Weekly Review (Sunday only)             │
  └─────────────────────────────────────────────────┘
```

---

## Partial Completion Protocol

```
End of every session, I say:
  "Done: [x, y]. Not done: [z]"

You respond:
  "Carried forward to Session [N+1]: [z] — this is FIRST priority next session."
  If 2+ items carried: "Suggest covering [item] in weekend session."
```

---

## Phase 1 — Restore & Build (Sessions 1–30)
> Fix AI dependency. Dart + Flutter from first principles. DSA starts. Package polished.

```
SESSIONS 1–5   ★ QUICK WIN FIRST
────────────────────────────────────────────────────────────────────────
DSA         │ Two Sum → Contains Duplicate → Valid Anagram (3 problems, Arrays begin)
Flutter     │ Dart: type system, null safety, collections, OOP from scratch
Project     │ Polish dynamic_ui_renderer:
            │   → Write proper README with demo GIF + architecture diagram
            │   → Add badges, usage examples, API reference
            │   → Add to LinkedIn Featured section
            │   This is the first visible win. Do it before writing SurveyFlow.
NO-AI       │ End: Write a Dart class + a function from pure memory
Interview   │ ✗ Not yet
★ RESULT    │ GitHub immediately looks serious. Most Flutter devs don't have a package.

SESSIONS 6–15
────────────────────────────────────────────────────────────────────────
DSA         │ Arrays (remaining 5) + Two Pointers (4) = 9 problems  [Total ~12]
Flutter     │ Dart async/await + Future + Stream + Isolates + compute — internals
            │ Flutter Widget tree → Element tree → RenderObject — how rendering works
Project     │ SurveyFlow repo created
            │ Clean Architecture folder structure coded from scratch (no template)
            │ Riverpod setup (understand each file before writing it)
            │ GoRouter setup (nested routes, guards)
NO-AI       │ End: code a StatefulWidget + lifecycle methods from memory
Interview   │ ✗ Not yet
Review      │ Sunday: What can I code without AI this week that I couldn't last week?

SESSIONS 16–30
────────────────────────────────────────────────────────────────────────
DSA         │ Sliding Window (5) + Stack (6) = 11 problems  [Total ~23]
Flutter     │ Keys — why they matter (break app without them, then fix)
            │ InheritedWidget from scratch → understand what Riverpod replaces
            │ Riverpod: Provider internals → StateNotifier → AsyncNotifier
            │ (No code generation first — understand the generated code)
Project     │ Auth (Field Officer, Manager, Admin — all 3 roles)
            │ Dynamic form screen powered by dynamic_ui_renderer
            │ QR code scanner → pre-fill form fields
NO-AI       │ End: code a full StateNotifier + Provider from memory
Interview   │ STAR behavioral starts: Story 1 (Irish govt app) + Story 2 (farmers offline)
System D    │ ✗ Not yet
Review      │ Sunday: Can I explain Riverpod internals without looking anything up?
```

---

## Phase 2 — Deepen & Prepare (Sessions 31–60)
> Project becomes complex. Mock interviews running. System design starts.

```
SESSIONS 31–45
────────────────────────────────────────────────────────────────────────
DSA         │ Binary Search (7) + Linked List (6) = 13 problems  [Total ~36]
Flutter     │ Dio: interceptors, auth token refresh, retry logic from scratch
            │ Repository pattern: code the layers, understand why they exist
            │ Hive from scratch: boxes, type adapters, why it's fast
            │ Drift/SQLite: tables, queries, migrations from scratch
Project     │ Offline sync + background queue (Hive)
            │ Conflict resolution strategy (last-write-wins + merge cases)
            │ GPS location picker + offline map tile caching
            │ Multi-file upload with progress tracking + exponential backoff retry
NO-AI       │ End: code a full offline queue handler from memory
Interview   │ Flutter technical mocks START: 1/week. Score every answer.
System D    │ START: API design, pagination strategies, caching patterns
Behavioral  │ Stories 3–5: dynamic_ui_renderer story, disagreement, production failure
Review      │ Sunday: Mock scores improving? Offline sync working end-to-end?

SESSIONS 46–60
────────────────────────────────────────────────────────────────────────
DSA         │ Trees (11 problems)  [Total ~47]
Flutter     │ Performance: DevTools profiling hands-on + RepaintBoundary + Isolates
            │ GoRouter advanced: nested + redirect + guards from scratch
            │ AnimationController internals + implicit vs explicit animations
            │ CustomPainter: build a real chart
Project     │ WebSocket integration (real-time collaboration signal)
            │ Cursor-based pagination on submissions list (infinite scroll)
            │ Advanced search + filter with debouncing (Riverpod + server-side)
            │ Caching layer: stale-while-revalidate pattern
            │ Biometric auth (local_auth, understand platform channel behind it)
NO-AI       │ End: implement cursor pagination logic from memory
Interview   │ Flutter technical + System design mock (1/week each)
System D    │ Offline-first deep dive (teach me every trade-off in what I've already built)
Behavioral  │ Stories 6–8: timezone/culture, ambiguous requirements, why international
★ MILESTONE │ Session 60:
            │   Resume: final version
            │   LinkedIn: polished, Featured has package + project
            │   GitHub: SurveyFlow README with architecture diagram + screenshots
            │   Project: core features working end-to-end
Review      │ Sunday: Am I ready to apply? Honest self-check against each market.
```

---

## Phase 3 — Launch (Sessions 61–80)
> First applications sent. Real interviews. All tracks running.

```
SESSIONS 61–80
────────────────────────────────────────────────────────────────────────
DSA         │ Tries (3) + Heap (4) + Backtracking (4) = 11  [Total ~58]
Flutter     │ Testing: unit → widget → golden → Patrol integration from scratch
            │ Platform channels: MethodChannel + EventChannel
            │ Firebase: Firestore query optimization + Security Rules
            │ Feature flags (Remote Config)
Project     │ Real-time dashboard (Firestore streams + Riverpod StreamProvider)
            │ Push notifications (FCM, deep linking)
            │ Digital signature capture (CustomPainter → image export)
            │ Analytics charts (fl_chart from scratch)
            │ PDF report generation
            │ CI/CD pipeline: GitHub Actions + test gate + Fastlane
NO-AI       │ End: simulate 20-min live coding challenge under pressure
Interview   │ 2–3 full mocks/week. EVERY real interview → file → debrief.
System D    │ Real-time systems, full whiteboard mocks
★ APPLYING  │ START — priority order:
            │
            │  1. IRELAND
            │     → LinkedIn, Jobs.ie
            │     → "I currently work for an Irish company" = instant door opener
            │     → Target: govtech, enterprise, fintech, SaaS companies
            │     → Interview style: architecture + real-world, minimal LeetCode
            │
            │  2. UAE / QATAR
            │     → LinkedIn (DMs work well here)
            │     → Lead with: government app + farmers scale story
            │     → Interview: what you built, who used it — rarely LeetCode
            │     → Tax-free salary: negotiate firmly after first offer
            │
            │  3. GERMANY / NETHERLANDS
            │     → LinkedIn, Xing, Stepstone
            │     → EU Blue Card path (salary threshold: ~€56k+)
            │     → Interview: clean code culture + system design + some LeetCode
            │
            │  4. AUSTRALIA
            │     → Seek.com, LinkedIn
            │     → TSS 482 visa — filter for sponsorship explicitly
            │     → Interview: balanced tech + behavioral, culture fit matters
            │
            │  5. REMOTE-EU
            │     → LinkedIn, Remote.io, WeWorkRemotely
            │     → Lead with AI tooling expertise (Claude Code, MCP) — rare angle
            │
            │  Rate: 5–10 applications/week
            │  Follow up every application after 7 days
Review      │ Sunday: Response rate? Interview patterns emerging?
```

---

## Phase 4 — Active Search (Sessions 81–100+)
> Interviews weekly. Blind 75 complete. Learning never stops.

```
SESSIONS 81–100+
────────────────────────────────────────────────────────────────────────
DSA         │ Graphs (6) + DP (11) + Greedy (3) + Bit Manipulation (3) = 23
            │ ★ BLIND 75 COMPLETE (~Session 95)
Flutter     │ Fill gaps based entirely on what real interviews expose
Project     │ SurveyFlow: remaining polish, record final demo video
Interview   │ 3x/week real + mock. Every session saved + debriefed.
APPLYING    │ 10–15/week. Track all. Pipeline never empty.
Network     │ 5 LinkedIn DMs/week to Flutter devs at target companies
            │ Comment on Flutter community posts (visibility builds over time)
NO-AI       │ LeetCode mediums, 20 min, zero assistance — simulate real interview
Review      │ Sunday: What patterns repeat in rejections? Adjust aggressively.
```

---

## SurveyFlow — Feature Map

```
FEATURE                              CONCEPT LEARNED
────────────────────────────────────────────────────────────────────────
Role-based auth (3 roles)          → Firebase Auth, permission architecture
Dynamic forms (dynamic_ui_renderer)→ SDUI, JSON→widget, form state
Offline sync + queue               → Hive, sync strategies, conflict resolution
Background sync                    → Periodic + connectivity-triggered
WebSocket integration              → dart:io WebSocket, when vs Firestore
Cursor-based pagination            → Why cursor > offset, infinite scroll
Advanced search + debounce         → Debounce pattern, multi-filter Riverpod
Caching (stale-while-revalidate)   → Cache-first vs network-first, TTL
Biometric auth                     → local_auth, platform channel under hood
QR code scanner                    → mobile_scanner, pre-fill form fields
GPS location picker + offline map  → Background location, offline tiles
Multi-file upload + progress       → Upload queue, chunked upload, progress streams
Digital signature                  → CustomPainter, image export
Real-time dashboard                → Firestore streams, StreamProvider
Push notifications                 → FCM, token management, deep linking
Analytics (fl_chart)               → Charts from scratch, data aggregation
PDF report export                  → pdf package, dynamic templates
Feature flags (Remote Config)      → Remote enable/disable, A/B testing
Full CI/CD                         → GitHub Actions, Fastlane, test gates
```

---

## Key Milestones

```
Session  5  ──── ★ dynamic_ui_renderer README polished + LinkedIn Featured
Session 15  ──── SurveyFlow repo live, Clean Architecture structure done
Session 25  ──── Auth + Dynamic forms (own package) + QR scanner working
Session 30  ──── 3 STAR stories ready + first behavioral mock done
Session 35  ──── Offline sync + background queue complete
Session 45  ──── GPS + multi-file upload + advanced search done
Session 55  ──── WebSocket + cursor pagination + caching layer done
Session 60  ──── ★ READY: Resume final, LinkedIn polished, GitHub clean
Session 61  ──── ★ FIRST JOB APPLICATION SENT
Session 65  ──── Real-time dashboard + push notifications + biometric auth
Session 70  ──── Analytics + PDF + CI/CD + UI polish + demo GIF
Session 75  ──── SurveyFlow fully complete. 5-min demo practiced.
Session 95  ──── ★ BLIND 75 COMPLETE
Session 100 ──── Offer stage
```

---

## Track Load Visual

```
                    Phase 1    Phase 2    Phase 3    Phase 4
                    (S1–30)    (S31–60)   (S61–80)   (S81–100+)
──────────────────────────────────────────────────────────────────────
NO-AI Zone (end)     █████      █████      █████      █████  ← ALWAYS LAST
DSA                  ████       ████       ████       ████
Flutter (scratch)    █████      ████       ███        ██
SurveyFlow Project   ████       █████      ████       ░
System Design        ░          ███        ████       ████
Interview Mocks      ░          ███        █████      █████
Applying             ░          ░          ████       █████
Networking           ░          ░          ███        █████
──────────────────────────────────────────────────────────────────────
░ = not started  █ = light  ███ = active  █████ = heavy focus
```

---

## The Interview Story (Practice Until Natural)

```
"I'm a Flutter developer with 4+ years of production experience.
 I ship apps used by 90%+ of Irish government agencies.
 I built an offline-first app for 10,000+ farmers in rural India and Africa —
 regions with zero internet.

 I published dynamic_ui_renderer — an open-source Flutter package for server-driven UI.
 Forms and screens change from the server without app store releases.
 95%+ test coverage. Live on pub.dev.

 I built SurveyFlow on top of it — a field inspection platform with
 offline sync, WebSocket real-time updates, cursor pagination, and a live dashboard.

 I'm looking for a senior Flutter role in [country] where I can bring
 this depth to a global product."
```

---

## Country-Specific Interview Notes

```
IRELAND    Resume: "Currently building Flutter apps for Irish government agencies"
           Interview style: Real-world architecture, minimal LeetCode
           Your edge: You already work here. This is your strongest market.

UAE/QATAR  No LeetCode usually. "What did you build? Who used it? How many users?"
           Your edge: Government + enterprise + scale story is exactly what they want
           Salary: negotiate firmly — tax-free is the frame, not just the number

GERMANY/NL Clean code culture. Some LeetCode mediums. System design matters.
           Your edge: Published package shows code quality discipline
           EU Blue Card: salary threshold ~€56k+, mention open to relocation

AUSTRALIA  Balanced tech + behavioral. Culture fit weighted heavily.
           Your edge: Delivered across 3 continents (India, Ireland, Africa)
           Platform: Seek.com first, then LinkedIn

REMOTE-EU  Self-management proof + async comms + documentation
           Your edge: Built this entire learning system = self-driven signal
           AI tooling (Claude Code, MCP) is rare in Flutter community
```

---

## Non-Negotiables

```
1. NO-AI zone — every session, last 25–30 min, zero exceptions
2. DSA — blind75.md order, never skip
3. Partial completion — always report done/not-done at session end
4. Weekly review — every Sunday, minimum 15 min
5. Every mock or real interview → saved to file → debriefed
6. LinkedIn post after every Flutter concept
7. Applications never stop once Phase 3 starts
8. Never catch up by doubling — just resume and carry forward
```

---

## Files Generated Per Track

```
./scratch/<week-N>/<topic>.md             ← every NO-AI session (end of session)
./dsa/<concept>/<problem>.md             ← every DSA problem
./flutter/<category>/<topic>.md          ← every Flutter concept
./interview/<category>/<slug>.md         ← every mock question
./interview/system-design/<slug>.md      ← every system design session
./interview/behavioral/<slug>.md         ← every STAR story
./reviews/week-<N>.md                    ← every Sunday
```
