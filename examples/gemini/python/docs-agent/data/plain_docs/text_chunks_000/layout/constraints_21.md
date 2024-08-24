code-excerpt "lib/main.dart (Example13)" replace="/(return |;)//g"?
dart
UnconstrainedBox(
  child: Container(color: red, width: 20, height: 50),
)
The screen forces the UnconstrainedBox to be exactly
the same size as the screen. However, the UnconstrainedBox
lets its child Container be any size it wants.
