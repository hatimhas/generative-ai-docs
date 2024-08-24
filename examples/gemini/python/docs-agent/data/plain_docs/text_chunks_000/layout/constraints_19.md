code-excerpt "lib/main.dart (Example11)" replace="/(return |;)//g"?
dart
Center(
  child: ConstrainedBox(
    constraints: const BoxConstraints(
      minWidth: 70,
      minHeight: 70,
      maxWidth: 150,
      maxHeight: 150,
    ),
    child: Container(color: red, width: 1000, height: 1000),
  ),
)
Center allows ConstrainedBox to be any size up to the
screen size. The ConstrainedBox imposes additional
constraints from its constraints parameter onto its child.
The Container must be between 70 and 150 pixels.
It wants to have 1000 pixels,
so it ends up having 150 (the maximum).
