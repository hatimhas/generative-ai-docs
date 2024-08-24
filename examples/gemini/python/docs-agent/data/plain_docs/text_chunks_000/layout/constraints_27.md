code-excerpt "lib/main.dart (Example19)" replace="/(return |;)//g"?
dart
const Center(
  child: FittedBox(
    child: Text('Some Example Text.'),
  ),
)
But what happens if you put the FittedBox inside of a
Center widget? The Center lets the FittedBox
be any size it wants, up to the screen size.
The FittedBox then sizes itself to the Text,
and lets the Text be any size it wants.
Since both FittedBox and the Text have the same size,
no scaling happens.
