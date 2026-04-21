# const vs final vs var

**Category:** dart
**Difficulty:** Beginner
**One-Line Summary:** `const` = compile-time frozen + canonicalized; `final` = runtime once; `var` = mutable.

---

## Deep Dive

### var
Mutable. Type inferred once at assignment.
```dart
var name = 'Jash';
name = 'Gowda'; // fine
```

### final
Assigned once, at **runtime**. Value determined when the line executes.
```dart
final now = DateTime.now(); // evaluated at runtime — different every run
final user = fetchUser();
```
Locks the **variable** (reference). Contents of the object can still change.
```dart
final list = [1, 2, 3];
list.add(4); // ✅ fine — reference is locked, not the list contents
```

### const
Value must be known at **compile time** — before the app runs.
```dart
const pi = 3.14159;
const name = 'Jashwanth';
const now = DateTime.now(); // ❌ COMPILE ERROR
```

Two things const does:
1. **Canonicalization** — identical const values share the same object in memory
2. **Deep immutability** — the object AND its contents are frozen

```dart
const a = [1, 2, 3];
const b = [1, 2, 3];
print(identical(a, b)); // true — same object

final c = [1, 2, 3];
final d = [1, 2, 3];
print(identical(c, d)); // false — two different objects

const list = [1, 2, 3];
list.add(4); // ❌ runtime error — contents frozen
```

---

## const Constructors

For a class to support `const` construction, ALL fields must be `final`.

```dart
class AppConfig {
  final String appName;
  final String version;
  final int maxRetries;

  const AppConfig({
    required this.appName,
    required this.version,
    required this.maxRetries,
  });

  String describe() => '$appName, $version, $maxRetries';
}

const app1 = AppConfig(appName: 'shani', version: '1.0', maxRetries: 1);
const app2 = AppConfig(appName: 'shani', version: '1.0', maxRetries: 1);

print(identical(app1, app2)); // true — canonicalized
print(app1.describe());       // shani, 1.0, 1
```

Flutter widgets (`Text`, `Padding`, `SizedBox`) all use const constructors. This is why `const Text('Hello')` is built once and reused across rebuilds — Flutter skips the diff check entirely.

---

## When to Use What

| Situation | Use |
|-----------|-----|
| Value known at compile time | `const` |
| Value determined at runtime, assigned once | `final` |
| Value changes over time | `var` |
| Class field set in constructor | `final` |
| Widget with no dynamic data | `const` constructor |

---

## Common Mistakes

- Using `hashCode ==` to check same object — use `identical()` instead
- Thinking `final` makes collections immutable — it only locks the reference
- Forgetting that const requires ALL fields to be final in a class
- Using `var` everywhere — prefer `final` by default, `const` when possible

---

## Interview Angle

- "What does const do at compile time?" → canonicalization + deep immutability
- "Why use const widgets in Flutter?" → built once, reused every rebuild, Flutter skips diff
- "Difference between final and const?" → runtime vs compile-time; reference lock vs deep freeze
- "Can you have a const class with a mutable field?" → No — all fields must be final

---

## LinkedIn Post

Just learned why `const` in Flutter isn't just a style preference — it's a performance decision.

`const` widgets are canonicalized: Flutter builds them once and reuses the same object across every rebuild. No diffing, no allocation.

`final` locks the reference. `const` freezes everything — the reference AND the contents.

Deep understanding > daily usage. #Flutter #Dart #MobileEngineering
