# Dart: Functions, Closures, Typedefs

- **Category:** dart
- **Difficulty:** Intermediate
- **One-Line Summary:** Functions are first-class objects in Dart; closures capture surrounding scope by reference; typedefs name function signatures for readable APIs.

---

## Functions

Functions are objects in Dart. Type: `Function`. Can be stored in variables, passed as arguments, returned from other functions.

```dart
int add(int a, int b) => a + b;

int Function(int, int) operation = add;
print(operation(2, 3)); // 5
```

### Three Parameter Styles

```dart
// 1. Positional required
void greet(String name) => print('Hi $name');

// 2. Named (use required to force, default value for optional)
void createUser({required String name, int age = 0}) { }
createUser(name: 'Jash', age: 28);

// 3. Positional optional
void log(String msg, [String? level]) { }
log('error');
log('error', 'WARN');
```

Rule: Named = `{}`. Optional positional = `[]`. Never mix both in the same function.

---

## Anonymous Functions

```dart
// Full
var multiply = (int a, int b) {
  return a * b;
};

// Arrow (single expression only)
var multiply = (int a, int b) => a * b;
```

Used as callbacks — the argument you pass to `.map()`, `.where()`, `.forEach()` is an anonymous function. The method itself is named; the callback is anonymous.

```dart
list.map((n) => n * 2)  // (n) => n * 2 is the anonymous function
```

---

## Closures

A closure is a function that captures variables from its surrounding scope — even after that scope has finished executing.

```dart
Function makeCounter() {
  int count = 0;       // lives in makeCounter's scope

  return () {          // closes over count
    count++;
    print(count);
  };
}

var counter = makeCounter();
counter(); // 1
counter(); // 2
counter(); // 3

var counter2 = makeCounter(); // separate count
counter2(); // 1
```

`makeCounter()` has returned but `count` survives on the heap because the inner function captured it.

### Closure Loop Bug (Interview Classic)

```dart
// BUG
List<Function> callbacks = [];
for (int i = 0; i < 3; i++) {
  callbacks.add(() => print(i)); // all closures capture the SAME i by reference
}
callbacks[0](); // 3 — expected 0
callbacks[1](); // 3 — expected 1
callbacks[2](); // 3 — expected 2
```

**Why:** Closures capture variables by reference, not by value. All three closures point to the same `i`. When the loop ends, `i == 3`, so all print 3.

```dart
// FIX
for (int i = 0; i < 3; i++) {
  final captured = i;            // new variable created per iteration
  callbacks.add(() => print(captured));
}
callbacks[0](); // 0 ✓
callbacks[1](); // 1 ✓
callbacks[2](); // 2 ✓
```

Each iteration creates a new `captured` variable. Each closure captures a separate variable.

**Interviewer answer:** "Closures capture by reference. All callbacks pointed to the same `i`, which was 3 after the loop. Fix: create a new `final` per iteration so each closure has its own variable."

---

## Higher-Order Functions

A function that takes a function or returns a function.

```dart
// Takes a function
List<T> transform<T>(List<T> list, T Function(T) fn) {
  return list.map(fn).toList();
}
var doubled = transform([1, 2, 3], (n) => n * 2); // [2, 4, 6]

// Returns a function
Function multiplierOf(int factor) {
  return (int n) => n * factor;
}
var triple = multiplierOf(3);
print(triple(5)); // 15
```

---

## Typedefs

A typedef is an alias for a function signature — not a new type, just a readable name.

```dart
// Without typedef — verbose
void execute(int Function(String, bool) processor) { }

// With typedef
typedef Processor = int Function(String, bool);
void execute(Processor processor) { }
```

### Real Flutter Usage

```dart
typedef OnSubmit = void Function(Map<String, dynamic> formData);
typedef OnError = void Function(String message);
typedef VoidCallback = void Function(); // built into Flutter SDK

class DynamicForm extends StatelessWidget {
  final OnSubmit onSubmit;
  final OnError? onError;

  const DynamicForm({required this.onSubmit, this.onError});
}
```

### Generic Typedef (Dart 2.13+)

```dart
typedef Parser<T> = T Function(String raw);

Parser<int> intParser = int.parse;
Parser<DateTime> dateParser = DateTime.parse;
```

---

## The `call()` Method

Any class with a `call()` method can be used like a function.

```dart
class Validator {
  final String field;
  Validator(this.field);

  bool call(String value) => value.isNotEmpty;
}

var validateName = Validator('name');
print(validateName('Jash')); // true — Dart calls .call() automatically
// same as: validateName.call('Jash')
```

---

## Common Mistakes

- Thinking `.map()` is the anonymous function — it's not. The callback argument is.
- Closure loop bug: capturing a loop variable by reference.
- Typedef as "new type" — it's just an alias for a function signature.
- Using `[]` and `{}` params together in one function signature.

---

## Interview Angle

- "Explain the closure loop bug" — describe reference capture, show the fix with `final captured = i`
- "What is a typedef?" — alias for a function signature; makes APIs readable; not a new type
- "Are functions first-class in Dart?" — yes, type `Function`, can be stored/passed/returned
- Closures will come up again in mock interviews — flag for practice

---

## LinkedIn Post

```
Dart functions are first-class objects — you can store them, pass them, return them.

But the real power is closures: a function that remembers the variables around it, even after the outer function is gone.

Classic trap: the loop closure bug.
for (int i = 0; i < 3; i++) {
  callbacks.add(() => print(i)); // all print 3
}

All 3 closures captured the same i by reference. Fix: final captured = i inside the loop.

Typedef is just a named alias for a function signature — makes your widget APIs readable.
typedef OnSubmit = void Function(Map<String, dynamic> data);

Building SurveyFlow — these patterns are everywhere in form callbacks and state management.

#Flutter #Dart #MobileEngineering
```

---

## Related Topics

- Collections (map/where/reduce use anonymous functions heavily)
- async/await — Future callbacks use closures
- Riverpod — provider callbacks are closures
- dynamic_ui_renderer — form callbacks use typedef pattern
