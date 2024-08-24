code-excerpt "lib/main.dart (Example15)" replace="/(return |;)//g"?
dart
OverflowBox(
  minWidth: 0,
  minHeight: 0,
  maxWidth: double.infinity,
  maxHeight: double.infinity,
  child: Container(color: red, width: 4000, height: 50),
)
The screen forces the OverflowBox to be exactly the same
size as the screen, and OverflowBox lets its child Container
be any size it wants.
OverflowBox is similar to UnconstrainedBox;
the difference is that it won't display any warnings
if the child doesn't fit the space.
In this case, the Container has 4000 pixels of width,
and is too big to fit in the OverflowBox,
but the OverflowBox simply shows as much as it can,
with no warnings given.
