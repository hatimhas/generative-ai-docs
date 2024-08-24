code-excerpt "lib/main.dart (Example21)" replace="/(return |;)//g"?
dart
const Center(
  child: Text(
      'This is some very very very large text that is too big to fit a regular screen in a single line.'),
)
If, however, you remove the FittedBox, the Text
gets its maximum width from the screen,
and breaks the line so that it fits the screen.
