# Valid Anagram

- **Concept:** Arrays & Hashing
- **Difficulty:** Easy
- **Problem #:** 3 (Blind 75)

---

## Problem

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

```
s = "anagram", t = "nagaram" → true
s = "rat",     t = "car"     → false
```

---

## Key Pattern

Frequency map — count chars in s, decrement for chars in t, check all zeros.

---

## Intuition

Two strings are anagrams if and only if every character appears the same number of times in both. Build a frequency map from s, then subtract using t. If the map is all zeros at the end, they match.

---

## Brute Force

Sort both strings → compare. `O(n log n)` time, `O(1)` space. Simple but not optimal.

---

## Optimal Approach

1. Length check first — if lengths differ, immediately `false`
2. Loop through `s` → increment count for each char
3. Loop through `t` → decrement count for each char
4. Loop through map values → if any value != 0, return `false`

`O(n)` time, `O(1)` space (max 26 keys — fixed ceiling for lowercase English letters)

---

## My Code (with bug fixed)

```dart
void main() {
  print(isValidAnagram("anagram", "nagaram")); // true
  print(isValidAnagram("rat", "car"));         // false
  print(isValidAnagram("aab", "bba"));         // false
}

bool isValidAnagram(String s, String t) {
  if (s.length != t.length) return false;

  Map<String, int> charCount = {};

  for (var i = 0; i < s.length; i++) {
    charCount[s[i]] = (charCount[s[i]] ?? 0) + 1;
  }

  for (var i = 0; i < t.length; i++) {
    if (charCount.containsKey(t[i])) {
      charCount[t[i]] = charCount[t[i]]! - 1;
    }
  }

  for (var value in charCount.values) {
    if (value > 0) return false;
  }

  return true;
}
```

---

## Complexity

| | Complexity | Reason |
|--|--|--|
| Time | O(n) | 3 sequential loops — add, not multiply |
| Space | O(1) | Max 26 keys regardless of input size |

---

## Bug Found in Session

Wrote `hashmap[s[i]]` in loop 2 instead of `hashmap[t[i]]` — checked t but decremented s.
Breaks on inputs like `s = "aab"`, `t = "bba"` (returns true, should be false).

---

## Key Lesson: Sequential vs Nested Loops

- Sequential loops: `n + n + n = 3n → O(n)` — they add
- Nested loops: `n × n = n² → O(n²)` — they multiply

---

## Edge Cases

- Different lengths → false (caught immediately)
- All same characters (`"aaa"`, `"aaa"`) → true
- Characters in t not in s → skipped by containsKey, positive value remains in map → false
- Single character strings

---

## Interview Angle

**Q: Can you do it without extra space?**
Sort both → compare. But O(n log n) time trade-off. Interviewer wants to hear you know the trade-off.

**Q: What if input has Unicode, not just lowercase?**
Map still works. The O(1) space claim becomes O(k) where k = unique chars — still effectively constant for most real inputs.

**Q: Why O(1) space for the map?**
Lowercase English = max 26 keys. Fixed ceiling independent of n. That's the definition of O(1).

---

## Related Topics

- Two Sum (same frequency map concept)
- Contains Duplicate (same hashmap approach)
- Group Anagrams (next — sort key or frequency tuple as map key)
