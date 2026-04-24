# Top K Frequent Elements

- **Concept:** Arrays & Hashing + Bucket Sort
- **Difficulty:** Medium
- **Status:** Done

---

## Problem

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements.

```
Input:  nums = [1,1,1,2,2,3], k = 2
Output: [1, 2]

Input:  nums = [1], k = 1
Output: [1]
```

---

## Key Pattern

**Bucket Sort** — use frequency as the index into a list of lists.
Frequency can never exceed `n`, so bucket size is always `n+1`.

---

## Intuition

1. Build a frequency map: `{num: count}`
2. Create `n+1` buckets. Place each number into `bucket[its_frequency]`
3. Read buckets right-to-left (highest freq first), collect until you have `k` elements

---

## Approach 1 — Brute Force (Sort)

Build freq map, sort entries by value descending, take first k keys.

**Time:** O(n log n) | **Space:** O(n)

```dart
List<int> topKelements(List<int> nums, int k) {
  List<int> res = [];
  Map<int, int> frequency = {};

  for (int num in nums) {
    frequency[num] = (frequency[num] ?? 0) + 1;
  }

  var sortedFreq = frequency.entries.toList()
    ..sort((a, b) => b.value.compareTo(a.value));

  for (var i = 0; i < k; i++) {
    res.add(sortedFreq[i].key);
  }

  return res;
}
```

---

## Approach 2 — Optimal (Bucket Sort)

**Time:** O(n) | **Space:** O(n)

```dart
List<int> topKelements(List<int> nums, int k) {
  List<int> res = [];
  Map<int, int> frequency = {};

  // Step 1: build frequency map
  for (int num in nums) {
    frequency[num] = (frequency[num] ?? 0) + 1;
  }

  // Step 2: bucket[i] = all numbers that appear exactly i times
  List<List<int>> bucket = List.generate(nums.length + 1, (_) => []);
  for (var freq in frequency.entries) {
    bucket[freq.value].add(freq.key);
  }

  // Step 3: read right to left (highest freq first), collect k elements
  for (int i = bucket.length - 1; i >= 0; i--) {
    if (bucket[i].isEmpty) continue;
    for (var num in bucket[i]) {
      res.add(num);
    }
    if (res.length == k) break;
  }

  return res;
}
```

---

## Complexity

| Approach    | Time       | Space |
|-------------|------------|-------|
| Sort        | O(n log n) | O(n)  |
| Bucket Sort | O(n)       | O(n)  |

---

## Edge Cases

- `k = 1` — single most frequent element
- All elements equally frequent — any k of them is valid
- Tie at Kth position — problem guarantees unique answer (mention this in interviews)

---

## Common Mistakes

- Checking `frequency >= k` instead of ranking by frequency (wrong condition)
- Reusing loop variable `i` in nested loops (shadowing bug)
- Using `List<int>` for buckets instead of `List<List<int>>`

---

## Interview Angle

- "Why bucket sort over heap?" — O(n) vs O(n log k); bucket sort exploits the bounded frequency constraint
- "What if there's a tie at position k?" — problem guarantees unique answer; in general you'd return any valid set
- "Could you use a min-heap of size k?" — yes, O(n log k), a valid third approach worth mentioning

---

## Notes

Session 5. First attempt used `frequency >= k` as condition — incorrect (checks if count ≥ k, not top-K ranking).
Key fix: sort by value then take first k, then upgraded to bucket sort.
Variable shadowing bug in nested loop: used `i` for both outer and inner — fixed with `for (var num in bucket[i])`.
