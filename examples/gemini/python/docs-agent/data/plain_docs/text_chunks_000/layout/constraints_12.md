code-excerpt "lib/main.dart (Example4)" replace="/(return |;)//g"?
dart
Align(
  alignment: Alignment.bottomRight,
  child: Container(width: 100, height: 100, color: red),
)
This is different from the previous example in that it uses
Align instead of Center.
Align also tells the Container that it can be any size it
wants, but if there is empty space it won't center the Container.
Instead, it aligns the container to the bottom-right of the
available space.
