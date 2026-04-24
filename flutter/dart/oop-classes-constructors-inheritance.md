# OOP From Scratch — Classes, Constructors, Inheritance, Mixins

- **Category:** dart
- **Difficulty:** Intermediate
- **One-Line Summary:** Dart is single-inheritance, class-based OOP where everything is an object — no primitives exist.

---

## Deep Dive

### Everything Is an Object
No primitives in Dart. `int`, `double`, `bool`, `String` are all objects with methods and properties.

```dart
int x = 5;
x.toString(); // ✅ works — int is an object
x.isEven;     // ✅ property access
```

---

### Classes
A class defines fields (data), methods (behaviour), and constructors (how to create it).

```dart
class User {
  String name;
  int age;
  User(this.name, this.age); // initializing formal — Dart sugar
}
```

---

### 4 Types of Constructors

**1. Generative (default)**
```dart
class Point {
  double x, y;
  Point(this.x, this.y);
}
```

**2. Named Constructor** — multiple creation paths
```dart
Point.origin() : x = 0, y = 0;
Point.fromMap(Map<String, double> map) : x = map['x']!, y = map['y']!;
```

**3. `const` Constructor** — compile-time constant; all fields must be `final`
```dart
class Color {
  final int r, g, b;
  const Color(this.r, this.g, this.b);
}
const red = Color(255, 0, 0);
```
> `final` = assigned once at runtime. `const` = value known and locked at **compile time**.

**4. Factory Constructor** — doesn't always create new instance; can return cached/singleton
```dart
class Logger {
  static final Logger _instance = Logger._internal();
  factory Logger() => _instance;
  Logger._internal();
}
```

---

### Initializer List
Runs **before** constructor body. Required when `final` fields need computation.

```dart
class Circle {
  final double radius;
  final double area;
  Circle(double r)
      : radius = r,
        area = 3.14159 * r * r;
}
```
Order: initializer list → constructor body.

---

### Inheritance
Single inheritance only. `super(...)` call goes in initializer list.

```dart
class Animal {
  String name;
  Animal(this.name);
  void speak() => print('...');
}

class Dog extends Animal {
  Dog(String name) : super(name);

  @override
  void speak() => print('$name barks');
}
```

Named parent constructor → `super` must use named param:
```dart
// parent: Vehicle({required this.brand})
Car(String brand) : super(brand: brand); // ✅ named
// NOT: super(brand)                      // ❌ positional
```

---

### Abstract Classes
Can't be instantiated. Define contracts. Can have both abstract and concrete methods.

```dart
abstract class Shape {
  double area();                               // abstract — no body
  void describe() => print('Area: ${area()}'); // concrete — has body
}
```

---

### Interfaces — Every Class Is One
No `interface` keyword. Every class implicitly defines one.

```dart
class Swimmer {
  void swim() => print('swimming');
}

class Duck implements Swimmer {
  @override
  void swim() => print('duck swims'); // must implement everything
}
```

---

### Mixins — Add Behaviour Without Inheritance
Solves the "behaviour from multiple sources" problem that single inheritance can't.

```dart
mixin Flyable {
  void fly() => print('$runtimeType is flying');
}

mixin Swimmable {
  void swim() => print('$runtimeType is swimming');
}

class Duck extends Animal with Flyable, Swimmable {
  Duck(String name) : super(name);
}
```

Rules: no generative constructor. Can use `on SomeClass` to restrict usage.

---

### Mental Model

| Keyword | Purpose | Multiple? |
|---------|---------|-----------|
| `extends` | Inherit implementation + interface | No |
| `implements` | Adopt interface only — implement everything yourself | Yes |
| `with` | Add mixin behaviour | Yes |

---

## Common Mistakes

- Calling `super(...)` in constructor body instead of initializer list — compile error
- Forgetting `brand: brand` (named param) when parent uses named constructor
- Non-`final` field in `const` constructor — compile error
- Using `extends` when you only want the interface → use `implements`

---

## Interview Angle

- *"What's the difference between extends and implements in Dart?"*
- *"Why must const constructor fields be final?"*
- *"How do mixins differ from inheritance? When would you use one?"*
- *"Can a class extend multiple classes in Dart? How do you work around that?"*

---

## Related Topics
- `const` vs `final` vs `var`
- Mixins with `on` clause
- `@immutable` annotation
- Riverpod providers (use factory pattern internally)
