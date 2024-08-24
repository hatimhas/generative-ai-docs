code-excerpt "lib/main.dart (Example2)" replace="/(return |;)//g"?
dart
Container(width: 100, height: 100, color: red)
The red Container wants to be 100 × 100,
but it can't, because the screen forces it to be
exactly the same size as the screen.
So the Container fills the screen.
