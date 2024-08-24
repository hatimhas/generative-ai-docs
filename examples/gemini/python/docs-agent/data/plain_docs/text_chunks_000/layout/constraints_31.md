code-excerpt "lib/main.dart (Example23)" replace="/(return |;)//g"?
dart
Row(
  children: [
    Container(color: red, child: const Text('Hello!', style: big)),
    Container(color: green, child: const Text('Goodbye!', style: big)),
  ],
)
The screen forces the Row to be exactly the same size
as the screen.
Just like an UnconstrainedBox, the Row won't
impose any constraints onto its children,
and instead lets them be any size they want.
The Row then puts them side-by-side,
and any extra space remains empty.
