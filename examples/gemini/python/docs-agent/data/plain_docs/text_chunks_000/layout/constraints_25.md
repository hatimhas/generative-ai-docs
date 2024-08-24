code-excerpt "lib/main.dart (Example17)" replace="/(return |;)//g"?
dart
UnconstrainedBox(
  child: LimitedBox(
    maxWidth: 100,
    child: Container(
      color: Colors.red,
      width: double.infinity,
      height: 100,
    ),
  ),
)
Here you won't get an error anymore,
because when the LimitedBox is given an
infinite size by the UnconstrainedBox;
it passes a maximum width of 100 down to its child.
If you swap the UnconstrainedBox for a Center widget,
the LimitedBox won't apply its limit anymore
(since its limit is only applied when it gets infinite
constraints), and the width of the Container
is allowed to grow past 100.
This explains the difference between a LimitedBox
and a ConstrainedBox.
