code-excerpt "lib/main.dart (Example5)" replace="/(return |;)//g"?
dart
Center(
  child: Container(
      width: double.infinity, height: double.infinity, color: red),
)
The screen forces the Center to be exactly the
same size as the screen, so the Center fills the screen.
The Center tells the Container that it can be any size it wants,
but not bigger than the screen. The Container wants to be
of infinite size, but since it can't be bigger than the screen,
it just fills the screen.
