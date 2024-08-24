code-excerpt "lib/main.dart (Example18)" replace="/(return |;)//g"?
dart
const FittedBox(
  child: Text('Some Example Text.'),
)
The screen forces the FittedBox to be exactly the same
size as the screen. The Text has some natural width
(also called its intrinsic width) that depends on the
amount of text, its font size, and so on.
The FittedBox lets the Text be any size it wants,
but after the Text tells its size to the FittedBox,
the FittedBox scales the Text until it fills all of
the available width.
