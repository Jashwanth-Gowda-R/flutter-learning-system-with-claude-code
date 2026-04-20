# Two Sum

- **Concept:** Arrays & Hashing
- **Difficulty:** Easy
- **Status:** Done

## Key Pattern
Complement lookup — store `{value: index}`, check if `target - current` already exists.

## Intuition
Instead of scanning the whole array for each element (O(n²)), store what you've seen in a hash map. For each number, ask: "Is the value I need to pair with this already in the map?" One pass, O(1) lookup each time.

## Brute Force
```dart
// Two nested loops — check every pair
// O(n²) time, O(1) space
for (int i = 0; i < nums.length; i++) {
  for (int j = i + 1; j < nums.length; j++) {
    if (nums[i] + nums[j] == target) return [i, j];
  }
}
```

## Optimal Approach
Store `{value → index}` as you iterate. Before storing, check if `target - nums[i]` is already in the map.

**Why `{value: index}` not `{index: value}`?**
You look up by value ("have I seen 3 before?"), so value must be the key.

## My Code (written without AI)
```dart
List<int> twoSum(List<int> nums, int target) {
  Map<int, int> hashmap = {};

  for (var i = 0; i < nums.length; i++) {
    int required = target - nums[i];
    if (hashmap.containsKey(required)) {
      return [i, hashmap[required]!];
    }
    hashmap[nums[i]] = i;
  }

  return []; // problem guarantees a solution exists
}
```

## Complexity
- Time: O(n) — single pass
- Space: O(n) — map stores up to n entries

## Edge Cases
- Duplicate values that form the answer: `[3,3], target=6` → works because we check before storing
- Negative numbers: works, hash map handles any int key
- Two-element array: works, caught on second iteration

## Common Mistakes
- Storing `{index: value}` then trying `hashmap[required]` — gets you nothing useful
- Using `containsValue` instead of `containsKey` — O(n) per lookup, defeats the purpose
- Forgetting `!` on map lookup return (Dart returns `int?`, not `int`)

## Interview Angle
- "Why not sort + two pointers?" → sorting destroys original indices; need extra bookkeeping, still O(n log n)
- "What if there are duplicates?" → check before store; problem guarantees exactly one solution
- "What's the trade-off?" → O(n) space for O(n) time gain vs O(1) space brute force

## Notes
- First problem. Identified the {value: index} vs {index: value} trap on own after a hint. Good.
- Typed the map correctly after review (`Map<int, int>` not `Map`).
