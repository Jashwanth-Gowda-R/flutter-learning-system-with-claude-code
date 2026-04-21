# Dart Collections

- **Category:** dart
- **Difficulty:** Beginner → Intermediate
- **One-Line Summary:** List (ordered, indexed), Map (key-value, O(1) lookup), Set (unique, O(1) lookup) — all backed by hash tables except List.

---

## Deep Dive

### List

Ordered, indexed, allows duplicates.

```dart
List<String> names = ['Alice', 'Bob', 'Alice'];
```

- **Fixed vs growable:** `List.filled(3, 0)` is fixed length — `.add()` throws at runtime. `[]` is growable.
- **`const` list:** deeply immutable — no add, remove, or modify.
- **Spread operator:** `[...list1, ...list2]` creates a new list, original untouched.

### Map

Key-value pairs. Keys unique, values can repeat. O(1) lookup by key.

```dart
Map<String, int> scores = {'Alice': 90, 'Bob': 85};
scores['missing'];        // null — no crash
scores['missing'] ?? 0;   // safe default
scores['missing']!;       // crashes if null — only when certain
```

### Set

Unordered, no duplicates. O(1) membership check (hash table internally).

```dart
Set<String> tags = {'flutter', 'dart', 'flutter'}; // → {'flutter', 'dart'}
list.toSet().toList(); // deduplicate a list
```

**Set vs List for contains:**
- `set.contains(x)` → O(1)
- `list.contains(x)` → O(n) — scans every element

### Generics

Compile-time contract. Without generics you get `dynamic` — no type checking, no autocomplete, runtime crashes.

```dart
List names = ['Alice', 42];         // valid but dangerous
List<String> names = ['Alice', 42]; // compile error — caught early
Map<String, List<int>> grouped = {}; // complex generics work the same way
```

---

## When to Use

| Need | Use |
|------|-----|
| Ordered items, access by index | List |
| Key → value lookup, frequency count | Map |
| Unique items, fast membership check | Set |
| Type-safe collections | Always use generics |

---

## Sorting a Map by Value (Memorize This)

```dart
var sorted = freq.entries.toList()
  ..sort((a, b) => b.value.compareTo(a.value)); // descending
```

- `.entries` → Iterable of MapEntry(key, value)
- `.toList()` → makes it sortable
- `..sort(...)` → cascade: sorts in place, returns the list
- `b.compareTo(a)` → descending; `a.compareTo(b)` → ascending

---

## Class Architecture Rule

Build expensive state once in the constructor. Don't recompute in every method.

```dart
// Bad — map rebuilt on every call
bool contains(String word) {
  Map<String, int> freq = {};
  for (var w in words) { freq[w] = (freq[w] ?? 0) + 1; }
  return freq.containsKey(word);
}

// Good — compute once, reuse
class WordFrequency {
  final Map<String, int> _freq = {};
  WordFrequency({required List<String> words}) {
    for (var word in words) {
      _freq[word] = (_freq[word] ?? 0) + 1;
    }
  }
  bool contains(String word) => _freq.containsKey(word);
}
```

---

## Common Mistakes

- Using `list.contains()` in a hot loop — use Set instead
- Rebuilding a map in every method call instead of storing in constructor
- `map[key]!` when key might not exist — always ask: am I certain?
- Shadowing: naming a loop variable the same as a method parameter
- Redundant ternary: `x != null ? true : false` → just `x != null`

---

## Interview Angle

**Q: Why is Set lookup O(1) but List lookup O(n)?**
Set uses a hash table — key is hashed to a bucket directly. List has no index on values — must scan.

**Q: When would you use a Set over a List?**
Deduplication, membership checks in hot paths (e.g., visited nodes in BFS/DFS).

**Q: What's the difference between `const []` and `final list = []`?**
`const` = compile-time immutable, deeply frozen, canonicalized.
`final` = reference can't be reassigned, but contents can be mutated.

---

## Related Topics

- Valid Anagram (Map frequency pattern)
- Group Anagrams (Map with List values)
- Dart: const/final/var
- Dart: generics and type system
