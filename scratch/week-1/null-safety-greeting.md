# NO-AI Challenge — Session 1

- **Week:** 1
- **Session:** 1
- **Topic:** Dart null safety — formatUserGreeting
- **Time taken:** ~25 min

## Task Given

Write a Dart function `formatUserGreeting(String name, String? nickname, int? loginCount)` that:
- Uses nickname if present, else name
- Appends login count message or "First time here?" based on loginCount

## What I Coded

```dart
String formatUserGreeting(String name, String? nickname, int? loginCount) {
  late String result1;
  late String result2;
  if (nickname != null) {
    result1 = "Hey $nickname! Welcome back.";
  } else {
    result1 = "Hey $name.";  // BUG: should be "Hello $name."
  }
  if (loginCount == null || loginCount == 0) {
    result2 = " First time here?";
  } else {
    result2 = " You've logged in $loginCount times.";
  }
  print(result1 + result2);
  return result1 + result2;
}
```

## Where I Got Stuck

- Used `late` on local variables — not needed, compiler handles definite assignment
- Wrong string literal: "Hey" instead of "Hello" for the no-nickname case

## Score

**7/10**

## Improvement Notes

1. `late` is for class fields that can't be initialized in the constructor — NOT for local variables
2. Always reread the spec before finalizing — output string literals matter
3. Cleaner approach: ternary operators reduce boilerplate for simple if/else assignments
