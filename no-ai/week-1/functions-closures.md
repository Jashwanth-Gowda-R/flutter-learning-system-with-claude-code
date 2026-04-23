# NO-AI Challenge — Session 4

**Topic:** Functions, Closures, Typedefs
**Week:** 1
**Score:** 6/10

---

## Task

Write a Dart function `applyAll` that takes a `List<int>` and a `List<int Function(int)>` (a list of functions), and applies each function to every element in order.

Call it with two operations: double the number, then subtract 1.

Example: `applyAll([1, 2, 3], [fn1, fn2])` → `[1, 3, 5]`

---

## Final Code

```dart
void main() {
  int Function(int) fn1 = (n) => (n * 2);
  int Function(int) fn2 = (n) => n - 1;
  var res = applyAll([1, 2, 3], [fn1, fn2]);
  print(res); // [1, 3, 5]
}

List<int> applyAll(List<int> nums, List<int Function(int)> fns) {
  List<int> result = [];

  for (var num in nums) {
    int current = num;
    for (int Function(int) fn in fns) {
      current = fn(current);
    }
    result.add(current);
  }
  return result;
}
```

---

## Where I Got Stuck

- Could not start independently — needed the loop skeleton provided
- Wrote `fn((current * current) - 1)` — put the transformation logic inside the fn call instead of just passing `current`
- Concept blocker: "fn is just a callable variable, call it with fn(arg)" was not intuitive initially

## Time Taken

~35 min (10 min independent attempt + guided completion)

## Key Miss

A function stored in a variable is called exactly like any other function — just `fn(arg)`. No special syntax. The variable name changes, the `()` calling syntax does not.

## Improvement Notes

- Next time: try writing the inner loop first — `fn(current)` — before worrying about the outer loop
- Closures and callable variables need more repetition — flagged for mock interview drill
