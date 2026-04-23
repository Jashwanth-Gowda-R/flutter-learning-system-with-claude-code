# NO-AI Challenge — Session 3

- **Week:** 1
- **Topic:** WordFrequency class (collections + map sorting)
- **Score:** 6/10

---

## Task Given

Write a `WordFrequency` class:
- Constructor takes `List<String> words`
- `topN(int n)` → n most frequent words, descending
- `contains(String word)` → bool

---

## Code Written

```dart
class WordFrequency {
  final List<String> words;

  WordFrequency({required this.words});

  List<String> topN(int n) {
    Map<String, int> freq = {};
    for (var word in words) {
      freq[word] = (freq[word] ?? 0) + 1;
    }
    var freqListSorted = freq.entries.toList()
      ..sort((a, b) => b.value.compareTo(a.value));
    List<String> res = [];
    for (var i = 0; i < n; i++) {
      res.add(freqListSorted[i].key);
    }
    return res;
  }

  bool contains(String word) {
    Map<String, int> freq = {};
    for (var word in words) {
      freq[word] = (freq[word] ?? 0) + 1;
    }
    return freq[word] != null ? true : false;
  }
}
```

---

## Issues Found

| Issue | Severity |
|-------|----------|
| Used Google to look up `.sort()` comparator syntax | High — NO-AI violation |
| Map rebuilt in both methods — should build once in constructor | High — architectural mistake |
| Variable shadowing: loop `word` hides parameter `word` in `contains` | Medium |
| `freq[word] != null ? true : false` — redundant ternary | Low |

---

## Correct Version

```dart
class WordFrequency {
  final Map<String, int> _freq = {};

  WordFrequency({required List<String> words}) {
    for (var word in words) {
      _freq[word] = (_freq[word] ?? 0) + 1;
    }
  }

  List<String> topN(int n) {
    var sorted = _freq.entries.toList()
      ..sort((a, b) => b.value.compareTo(a.value));
    return sorted.take(n).map((e) => e.key).toList();
  }

  bool contains(String word) => _freq.containsKey(word);
}
```

---

## Key Miss

Sort comparator syntax: `(a, b) => b.value.compareTo(a.value)` — must memorize cold.
Class state should be built once in constructor, not recomputed per method call.

---

## Improvement Notes

Write the sort comparator 5 times from memory before next session.
Next NO-AI: no Google, no Stack Overflow — sit with it.
