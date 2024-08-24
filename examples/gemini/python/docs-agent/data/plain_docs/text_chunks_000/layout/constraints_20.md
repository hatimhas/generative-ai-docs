code-excerpt "lib/main.dart (Example12)" replace="/(return |;)//g"?
dart
Center(
  child: ConstrainedBox(
    constraints: const BoxConstraints(
      minWidth: 70,
      minHeight: 70,
      maxWidth: 150,
      maxHeight: 150,
    ),
    child: Container(color: red, width: 100, height: 100),
  ),
)
Center allows ConstrainedBox to be any size up to the
screen size. The ConstrainedBox imposes additional
constraints from its constraints parameter onto its child.
The Container must be between 70 and 150 pixels.
It wants to have 100 pixels, and that's the size it has,
since that's between 70 and 150.
