code-excerpt "lib/main.dart (Example3)" replace="/(return |;)//g"?
dart
Center(
  child: Container(width: 100, height: 100, color: red),
)
The screen forces the Center to be exactly the same size
as the screen, so the Center fills the screen.
The Center tells the Container that it can be any size it
wants, but not bigger than the screen. Now the Container
can indeed be 100 × 100.
