# Product of Array Except Self

- **Concept:** Arrays & Hashing — Prefix/Suffix Products
- **Difficulty:** Medium
- **Status:** Done

---

## Problem

Given an integer array `nums`, return an array `output` where `output[i]` is the product of all elements **except** `nums[i]`.

**Constraints:** O(n) time. No division allowed.

```
Input:  [1, 2, 3, 4]
Output: [24, 12, 8, 6]
```

---

## Key Pattern

`output[i] = (product of everything LEFT of i) × (product of everything RIGHT of i)`

No division needed. Build prefix and suffix products separately.

---

## Why No Division?

Division fails when the array contains zero — dividing by zero throws an error.

---

## Brute Force

For each index, multiply all other elements. O(n²) time.

---

## Approach A — Two Arrays (O(n) space)

Build explicit `prefix[]` and `postfix[]` arrays, then multiply.

```dart
List<int> productExceptSelf(List<int> nums) {
  List<int> res = List.filled(nums.length, 1);
  List<int> prefix = List.filled(nums.length, 1);
  List<int> postfix = List.filled(nums.length, 1);

  int pre = 1;
  int post = 1;

  for (var i = 0; i < nums.length; i++) {
    prefix[i] = pre;
    pre = nums[i] * pre;
  }

  for (var i = nums.length - 1; i >= 0; i--) {
    postfix[i] = post;
    post = nums[i] * post;
  }

  for (var i = 0; i < nums.length; i++) {
    res[i] = prefix[i] * postfix[i];
  }

  return res;
}
```

- Time: O(n)
- Space: O(n) — two extra arrays

---

## Approach B — Optimal (O(1) extra space)

Reuse the output array for the prefix pass. Do the suffix in-place with a single running variable.

```dart
List<int> productExceptSelfOptimal(List<int> nums) {
  List<int> res = List.filled(nums.length, 1);
  int pre = 1;
  int post = 1;

  // Pass 1: store prefix products in res
  for (var i = 0; i < nums.length; i++) {
    res[i] = pre;
    pre *= nums[i];
  }

  // Pass 2: multiply suffix in-place
  for (var i = nums.length - 1; i >= 0; i--) {
    res[i] *= post;
    post *= nums[i];
  }

  return res;
}
```

- Time: O(n)
- Space: O(1) — output array doesn't count

---

## Trace (Optimal)

```
Input: [1, 2, 3, 4]

After prefix pass:  res = [1, 1, 2, 6]
After suffix pass:  res = [24, 12, 8, 6]  ✓
```

---

## Edge Cases

- Array with a zero: works correctly — prefix/suffix naturally handles it
- Array with two zeros: all outputs are 0
- Array of length 2: works — each element is just the other

---

## Interview Angle

> "Can you do it without division in O(n)?"
> "Can you reduce the space to O(1)?"

Always lead with the two-pass prefix/suffix pattern. Mention that the output array doesn't count toward space complexity.

---

## Spreadsheet Update

| Problem | Concept | Difficulty | Status |
|---|---|---|---|
| Product of Array Except Self | Arrays & Hashing — Prefix/Suffix | Medium | Done |
