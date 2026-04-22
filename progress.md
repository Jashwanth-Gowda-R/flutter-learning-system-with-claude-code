# Session Progress Tracker

> Updated automatically after every session. Source of truth for resuming after any gap.

## Current State

- **Session:** 4 (next)
- **Week:** 1
- **Phase:** 1 — Restore & Build

## Track Status

| Track | Last Completed | Next Up |
|-------|---------------|---------|
| DSA | Group Anagrams (Arrays & Hashing) — Done | Top K Frequent Elements |
| Flutter | Dart: collections (List, Map, Set, generics) — Done | Dart: functions, closures, typedefs |
| Project | — | Polish dynamic_ui_renderer README (Session 5) |
| System Design | Not started yet | — |
| Interview Mocks | Not started yet | — |
| Behavioral Stories | Not started yet | — |

## Carried Forward

- Flutter: Dart functions, closures, typedefs — carry to Session 5 morning
- NO-AI challenge (Session 4) — skipped, carry to Session 5

## NO-AI Zone Log

| Session | Topic | Score | Key Miss |
|---------|-------|-------|----------|
| 1 | formatUserGreeting (null safety) | 7/10 | Wrong string literal ("Hey" vs "Hello"); `late` misused on local vars |
| 2 | ThemeConfig (const constructor) | 10/10 | None — clean execution |
| 3 | WordFrequency class (collections + map sorting) | 6/10 | Used Google for sort comparator; map rebuilt per method instead of constructor |

## Weekly Application Count (starts Session 61)

| Week | Applications Sent | Responses |
|------|------------------|-----------|
| — | — | — |

## Notes

Session 3 complete. DSA: Valid Anagram saved at dsa/arrays-hashing/valid-anagram.md.
Flutter: collections saved at flutter/dart/collections.md.
NO-AI: 6/10 — used Google for .sort() comparator (violation); architectural issue: map rebuilt in every method.
Key concept: sequential loops add (O(n)), nested loops multiply (O(n²)). O(1) space when map has fixed ceiling.
Sort pattern to memorize: freq.entries.toList()..sort((a, b) => b.value.compareTo(a.value))

Session 4 DSA-only. Group Anagrams ✓. Flutter + NO-AI carried — life got in the way, no guilt.
