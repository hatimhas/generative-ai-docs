code-excerpt "lib/main.dart (Example14)" replace="/(return |;)//g"?
dart
UnconstrainedBox(
  child: Container(color: red, width: 4000, height: 50),
)
The screen forces the UnconstrainedBox to be exactly
the same size as the screen, and UnconstrainedBox
lets its child Container be any size it wants.
Unfortunately, in this case the Container is
4000 pixels wide and is too big to fit in
the UnconstrainedBox, so the UnconstrainedBox displays
the much dreaded "overflow warning".
