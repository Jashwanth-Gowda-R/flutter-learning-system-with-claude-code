# NO-AI Challenge — Session 5: OOP Animal Hierarchy

**Week:** 1
**Session:** 5
**Date:** 2026-04-26
**Score:** 8/10

---

## Task Given

Create an Animal hierarchy from memory:

1. Abstract class `Animal` with named constructor (name, sound), abstract `speak()`, concrete `describe()`
2. Mixin `CanFly` with `fly()` that prints "[name] is flying"
3. Class `Dog` extends `Animal` — implement `speak()`
4. Class `Bird` extends `Animal` with `CanFly` — implement `speak()`, can fly()
5. `main()` — create both, call all methods

---

## My Code

```dart
void main() {
  Dog dog = Dog('jashu', 'bark');
  dog.speak();
  dog.describe();

  Bird bird = Bird('kaka raja', 'chirpping');
  bird.speak();
  bird.describe();
  bird.fly(bird.name);
}

abstract class Animal {
  String name;
  String sound;
  Animal({required this.name, required this.sound});

  void speak();

  void describe() => print("I am $name");
}

mixin CanFly {
  void fly(String name) {
    print("$name is flying");
  }
}

class Dog extends Animal {
  Dog(String name, String sound) : super(name: name, sound: sound);

  @override
  void speak() {
    print("$name says $sound");
  }
}

class Bird extends Animal with CanFly {
  Bird(String name, String sound) : super(name: name, sound: sound);

  @override
  void speak() {
    print("$name says $sound");
  }

  @override
  void fly(String name) {
    print("$name is flying");
  }
}
```

---

## What Was Good

- Named constructor + `super(name: name, sound: sound)` — correct (key lesson from today's OOP session)
- Abstract class structure — abstract method + concrete method split correct
- Inheritance chain for Dog and Bird — clean
- `main()` runs correctly

## Key Miss

**Mixin misuse** — passed `name` as a parameter to `fly()` and overrode it in `Bird`.
This defeats the entire purpose of the mixin. If you override in every class, the mixin does nothing.

**Correct approach:**

```dart
mixin CanFly on Animal {
  void fly() => print("$name is flying");  // accesses Animal.name directly
}
```

`on Animal` constrains the mixin to Animal subclasses — gives direct access to `name`.
Bird then inherits `fly()` from the mixin without needing to override it.
Call in main: `bird.fly()` — no parameter.

---

## Improvement Notes

- `on SomeClass` constraint — use when mixin needs fields from the class it's applied to
- Never pass fields as parameters to mixin methods — that's a sign the mixin should be constrained with `on`
- Overriding a mixin method in every subclass = the mixin is pointless

---

## Time Taken

~25 min

## Trend

| Session | Topic | Score |
|---------|-------|-------|
| 1 | null safety greeting | 7/10 |
| 2 | const constructor | 10/10 |
| 3 | word frequency | 6/10 |
| 4 | functions/closures | 6/10 |
| 5 | OOP animal hierarchy | 8/10 |
