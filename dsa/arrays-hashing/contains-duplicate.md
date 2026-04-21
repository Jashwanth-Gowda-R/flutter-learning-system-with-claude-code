# Contains Duplicate

**Concept:** Arrays & Hashing
**Difficulty:** Easy
**Status:** Done

---

## Problem

Given an integer array `nums`, return `true` if any value appears at least twice, and `false` if every element is distinct.

```
Input: [1,2,3,1]           → true
Input: [1,2,3,4]           → false
Input: [1,1,1,3,3,4,3,2,4,2] → true
```

---

## Key Pattern

Membership tracking — "have I seen this before?"

---

## Intuition

If any element repeats, the set size will be smaller than the array size. Or: as you iterate, if an element already exists in your seen-set, you found a duplicate — exit immediately.

---

## Approaches

### Brute Force — O(n²) time, O(1) space
Nested loops: for every element, check all other elements.
```dart
for (int i = 0; i < nums.length; i++) {
  for (int j = i + 1; j < nums.length; j++) {
    if (nums[i] == nums[j]) return true;
  }
}
return false;
```

### Version 1 — Set length comparison — O(n) time, O(n) space
```dart
bool isDuplicateBrute(List<int> nums) {
  return nums.length != nums.toSet().length;
}
```
**Note:** `toSet()` allocates O(n) extra memory. NOT O(1) space.

### Version 2 (Optimal) — Set with early exit — O(n) time, O(n) space
```dart
bool isDuplicate(List<int> nums) {
  final seen = <int>{};
  for (final num in nums) {
    if (seen.contains(num)) return true;
    seen.add(num);
  }
  return false;
}
```
Early exit as soon as duplicate found. Use `Set` not `Map` — you only need membership, not key→value storage.

---

## Complexity

| Version | Time | Space |
|---------|------|-------|
| Brute force (nested loops) | O(n²) | O(1) |
| Set length comparison | O(n) | O(n) |
| Set with early exit | O(n) | O(n) |

---

## Can we do O(1) space?

Only if values are guaranteed in range `[1, n]`. Then negate `nums[abs(num)-1]` in-place — if already negative, it's a duplicate. LeetCode's Contains Duplicate has NO such constraint, so O(n) space is the best possible here. This technique applies to #287 Find the Duplicate Number.

---

## Edge Cases

- Single element array → false
- All same elements → true
- Negative numbers → handled by Set/HashMap correctly

---

## Common Mistakes

- Using `Map<int, int>` with value=1 when `Set<int>` is the right tool
- Thinking `toSet()` is O(1) space — it creates a new collection in memory
- Forgetting early exit optimization

---

## Interview Angle

- "Why Set over Map here?" → You only need membership check, not counting
- "What's the space trade-off?" → O(n) space to get O(n) time vs O(1) space at O(n²) time
- "Can you do better than O(n) space?" → Only with in-range constraint (negate in-place trick)
