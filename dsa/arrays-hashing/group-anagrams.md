# Group Anagrams

**Concept:** Arrays & Hashing
**Difficulty:** Medium
**Status:** Done

---

## Problem

Given an array of strings `strs`, group the anagrams together. Return the answer in any order.

```
Input:  ["eat","tea","tan","ate","nat","bat"]
Output: [["eat","tea","ate"],["tan","nat"],["bat"]]
```

---

## Key Pattern

Sort each string's characters → use as hashmap key. All anagrams produce the same sorted key.

---

## Intuition

Two strings are anagrams if and only if their sorted character sequences are identical.
Sort every string → same key → group them.

---

## Brute Force — O(n² × k)

For every pair, sort both and compare. O(n²) pairs × O(k log k) sort = too slow.

---

## Optimal Approach — O(n × k log k)

Single pass: sort each string's chars → key → append original to map[key].

```
"eat" → "aet" → map["aet"] = ["eat"]
"tea" → "aet" → map["aet"] = ["eat","tea"]
"tan" → "ant" → map["ant"] = ["tan"]
"ate" → "aet" → map["aet"] = ["eat","tea","ate"]
"nat" → "ant" → map["ant"] = ["tan","nat"]
"bat" → "abt" → map["abt"] = ["bat"]
```

---

## My Code (written without AI)

```dart
List<List<String>> groupAnagrams(List<String> strs) {
  List<List<String>> res = [];
  Map<String, List<String>> hashmap = {};

  for (var str in strs) {
    var originalString = str;
    var strList = str.split('');
    strList..sort((a, b) => a.compareTo(b));
    var strValue = strList.join();

    hashmap[strValue] ??= [];
    hashmap[strValue]?.add(originalString);
  }

  for (var value in hashmap.values) {
    res.add(value);
  }

  return res;
}
```

---

## Optimized Code

```dart
List<List<String>> groupAnagrams(List<String> strs) {
  final Map<String, List<String>> map = {};
  for (final str in strs) {
    final key = (str.split('')..sort()).join();
    (map[key] ??= []).add(str);
  }
  return map.values.toList();
}
```

---

## Complexity

- **Time:** O(n × k log k) — n strings, each sorted in O(k log k)
- **Space:** O(n × k) — all strings stored in the map

---

## Key Dart Lesson — Cascade vs Method Chain

```dart
// BROKEN — cascade returns original List, not the String from join()
var key = str.split('')
  ..sort()
  ..join();  // ← join result discarded, key is List<String>

// CORRECT — cascade sort mutates list, then .join() captures String result
var key = (str.split('')..sort()).join();
```

`..` always returns the receiver, not the result. Use `..` for mutations, then chain real methods outside the cascade.

---

## Edge Cases

- `[""]` → sorted `""` → map[""] = [""] → `[[""]]` ✓
- `["a"]` → sorted `"a"` → map["a"] = ["a"] → `[["a"]]` ✓
- All same anagram → one key, one group ✓
- All unique → each in its own group ✓

---

## Interview Angle

- "Why sort? Could you use a character frequency array as key instead?"
  → Yes: count[26] as key avoids sort, makes it O(n × k) instead of O(n × k log k)
- "What if strings contain unicode?" → sorted key still works; frequency array breaks

---

## Notes

Session 4. Solved independently. Used Google hint for cascade issue — caught and fixed self.
Score: 9/10. Logic perfect. Minor: typo in var name, `?.add` after `??=` (should be `!.add`).
