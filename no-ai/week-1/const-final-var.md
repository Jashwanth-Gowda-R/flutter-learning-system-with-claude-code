# NO-AI Challenge — const vs final vs var

**Session:** 2
**Week:** 1
**Topic:** ThemeConfig class with const constructor

---

## Task Given

Write a Dart class `ThemeConfig` from memory:
- `const` constructor
- Fields: `primaryColor` (String), `isDarkMode` (bool), `fontScale` (double)
- Method `summary()` → returns: `"Theme: {primaryColor} | Dark: {isDarkMode} | Scale: {fontScale}"`
- In `main()`: prove const-const identical, prove const-final NOT identical, call summary() on each

---

## Code Written

```dart
void main() {
  const theme1 = ThemeConfig(
    primaryColor: 'white',
    isDarkMode: true,
    fontScale: 1.5,
  );
  const theme2 = ThemeConfig(
    primaryColor: 'white',
    isDarkMode: true,
    fontScale: 1.5,
  );

  final theme3 = ThemeConfig(
    primaryColor: 'white',
    isDarkMode: true,
    fontScale: 1.5,
  );

  print(identical(theme1, theme2)); // true
  print(identical(theme1, theme3)); // false
  print(identical(theme2, theme3)); // false

  print(theme1.summary());
  print(theme2.summary());
  print(theme3.summary());
}

class ThemeConfig {
  final String primaryColor;
  final bool isDarkMode;
  final double fontScale;

  const ThemeConfig({
    required this.primaryColor,
    required this.isDarkMode,
    required this.fontScale,
  });

  String summary() =>
      "Theme: $primaryColor | Dark: $isDarkMode | Scale: $fontScale";
}
```

---

## Score: 10/10

## Where I Got Stuck
Nowhere — clean from memory.

## Key Win This Session
Applied `identical()` correction from AppConfig review immediately. No `hashCode` mistake repeated.

## Improvement Notes
- Session 1 miss: `late` on local variables (7/10)
- Session 2: zero mistakes (10/10)
- Trend: corrections are landing same session
