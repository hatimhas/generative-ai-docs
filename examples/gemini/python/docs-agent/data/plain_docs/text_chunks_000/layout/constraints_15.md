code-excerpt "lib/main.dart (Example7)" replace="/(return |;)//g"?
dart
Center(
  child: Container(
    color: red,
    child: Container(color: green, width: 30, height: 30),
  ),
)
The screen forces the Center to be exactly the same
size as the screen, so the Center fills the screen.
The Center tells the red Container that it can be any size
it wants, but not bigger than the screen. Since the red
Container has no size but has a child,
it decides it wants to be the same size as its child.
The red Container tells its child that it can be any size
it wants, but not bigger than the screen.
The child is a green Container that wants to
be 30 × 30. Given that the red Container sizes itself to
the size of its child, it is also 30 × 30.
The red color isn't visible because the green Container
entirely covers the red Container.
