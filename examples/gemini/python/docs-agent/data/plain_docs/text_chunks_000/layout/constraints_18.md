code-excerpt "lib/main.dart (Example10)" replace="/(return |;)//g"?
dart
Center(
  child: ConstrainedBox(
    constraints: const BoxConstraints(
      minWidth: 70,
      minHeight: 70,
      maxWidth: 150,
      maxHeight: 150,
    ),
    child: Container(color: red, width: 10, height: 10),
  ),
)
Now, Center allows ConstrainedBox to be any size up to
the screen size. The ConstrainedBox imposes additional
constraints from its constraints parameter onto its child.
The Container must be between 70 and 150 pixels.
It wants to have 10 pixels,
so it ends up having 70 (the minimum).
