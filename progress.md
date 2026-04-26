# Session Progress Tracker

> Updated automatically after every session. Source of truth for resuming after any gap.

## Current State

- **Session:** 5 (complete)
- **Week:** 1
- **Phase:** 1 — Restore & Build

## Track Status

| Track | Last Completed | Next Up |
|-------|---------------|---------|
| DSA | Top K Frequent Elements (Arrays & Hashing) — Done | Product of Array Except Self |
| Flutter | Dart: OOP — classes, constructors (4 types), inheritance, abstract, interfaces, mixins ✓ | Dart: async/await, Future, Stream |
| Project | — | Session 15: Repo setup, Clean Architecture, Riverpod + GoRouter |
| System Design | Not started yet | — |
| Interview Mocks | Not started yet | — |
| Behavioral Stories | Not started yet | — |

## Carried Forward

- Clean start

## NO-AI Zone Log

| Session | Topic | Score | Key Miss |
|---------|-------|-------|----------|
| 1 | formatUserGreeting (null safety) | 7/10 | Wrong string literal ("Hey" vs "Hello"); `late` misused on local vars |
| 2 | ThemeConfig (const constructor) | 10/10 | None — clean execution |
| 3 | WordFrequency class (collections + map sorting) | 6/10 | Used Google for sort comparator; map rebuilt per method instead of constructor |
| 4 | applyAll (functions, closures, callable variables) | 6/10 | Could not start independently; put logic inside fn() call; blocker: fn(arg) calling syntax |
| 5 | OOP Animal hierarchy | 8/10 | Mixin misuse — passed name as param + overrode in Bird; use `mixin X on Animal` instead |

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

Session 4 DSA-only (morning). Session 4 evening: Flutter functions/closures/typedefs + NO-AI done.
Flutter saved at flutter/dart/functions-closures-typedefs.md. NO-AI saved at no-ai/week-1/functions-closures.md.
NO-AI score 6/10 — callable variable syntax was the blocker. Closures flagged for mock interview drill.
Session 5: DSA only done. Top K Frequent Elements — bucket sort O(n). Saved at dsa/arrays-hashing/top-k-frequent-elements.md.
Session 5 (resumed): Flutter OOP done — classes, 4 constructor types, initializer list, inheritance, abstract classes, interfaces, mixins. Saved at flutter/dart/oop-classes-constructors-inheritance.md. Comprehension check passed. Key fix noted: named super constructor requires named param (super(brand: brand) not super(brand)).
Session 5 (after-dinner): Project README skipped (user decision). NO-AI done — 8/10. Key miss: mixin `on Animal` constraint not used; passed name as parameter instead. Saved at no-ai/week-1/oop-animal-hierarchy.md. Session 5 fully complete.
