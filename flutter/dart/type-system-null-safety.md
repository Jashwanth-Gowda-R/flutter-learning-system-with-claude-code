# Dart Type System + Null Safety

- **Topic:** Type System + Null Safety
- **Category:** dart
- **Difficulty:** Beginner → Intermediate
- **One-Line Summary:** Dart's sound type system + null safety guarantee at compile time that type violations and null crashes cannot happen at runtime.

---

## Deep Dive

### Why Dart's Type System is "Sound"
Dart is statically typed with type inference. Types are locked at compile time — no runtime type juggling like JavaScript. "Sound" means: if the code compiles clean, type violations cannot occur at runtime. This enables Flutter's performance — no runtime type-checking overhead.

### Null Safety — The Core Problem It Solves
Before Dart 2.12, `String name = null` was legal. The compiler couldn't catch it. Apps crashed in production when `.length` was called on null. Null safety moves this failure from runtime → compile time.

### Nullable vs Non-nullable
```dart
String name = "Jash";   // compiler GUARANTEES never null
String? name = null;    // compiler FORCES you to handle null before use
```
The `?` is a compile-time annotation — zero runtime cost.

### The 4 Null Safety Operators
```dart
String? value = someFunction();

// 1. if-check (smart cast — compiler narrows type inside the block)
if (value != null) {
  print(value.length); // safe
}

// 2. ?? null coalescing
String result = value ?? "default";

// 3. ??= assign only if null
value ??= "fallback";

// 4. ! null assertion (you promise it's not null — runtime crash if wrong)
print(value!.length); // use sparingly — every ! is a promise you might break
```

### late keyword
```dart
late String userId; // non-nullable, not set yet — compiler trusts you

// Use for: things that can't be set in constructor (initState, post-auth values)
// Do NOT use: as a workaround for nullable — that defeats null safety
```

**`late` vs `?` decision rule:**
- Use `late` when: logically non-null, but technically can't be set in constructor (e.g. AnimationController in initState, auth token after login)
- Use `?` when: genuinely might not have a value during the object's lifecycle

---

## Code Example (written in session, no AI)

```dart
void main() {
  UserProfile user = UserProfile(name: 'shani');
  user.sessionToken = '123456'; // set after construction — simulates post-login
  user.display();
}

class UserProfile {
  String name;          // non-nullable — guaranteed always has a value
  String? bio;          // nullable — may or may not exist
  late String sessionToken; // non-nullable but set after construction

  UserProfile({required this.name, this.bio});

  void display() {
    print(name);
    if (bio != null) {
      print(bio);
    } else {
      print('No bio set');
    }
    print(sessionToken);
  }
}
```

**Session mistake to remember:** Do not combine `late` + `required` in constructor — if you set it in the constructor, just use a regular non-nullable field. `late` is only for post-construction assignment.

---

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| `late` + `required` in constructor | Defeats the purpose of `late` — just use a normal non-nullable field |
| Overusing `!` assertion | Every `!` can crash at runtime — handle null properly instead |
| Using `?` for everything "to be safe" | Makes your API lying — if a value is always set, model it as non-nullable |
| `if (bio != null) print(bio!)` | Don't need `!` inside a null check — compiler already knows |

---

## Interview Angle

**EU/Gulf/AUS interviewers ask:**
- "What is sound null safety and how does Dart enforce it?"
- "When would you use `late` vs a nullable type?"
- "What does the `!` operator do and when is it a code smell?"
- "How did null safety change how you write Dart code?"

**Your real answer hook:** "Before null safety, we had production crashes that were hard to trace. Null safety moved those failures to compile time — in my Irish govt app, it caught several potential null derefs during code review before they ever shipped."

---

## LinkedIn Post

> Dart's null safety isn't just syntax sugar — it's a compiler guarantee.
>
> `String name` = the compiler *proves* this is never null before your app runs.
> `String? name` = the compiler *forces* you to handle the null case.
>
> The result: a whole class of runtime crashes becomes compile-time errors.
>
> After using it daily for 2+ years, the mental model shift is: stop thinking about nulls at runtime. Think about your data contracts at design time.
>
> #Flutter #Dart #NullSafety #MobileDev

---

## Related Topics
- `const` vs `final` vs `var` (next session)
- Dart collections + generics
- async/await + Future (nullable return types are common here)
