A CurvedAnimation defines the animation's progress
as a non-linear curve.
code-excerpt "animate5/lib/main.dart (CurvedAnimation)"?
dart
animation = CurvedAnimation(parent: controller, curve: Curves.easeIn);
:::note
The Curves class defines many commonly used curves,
or you can create your own. For example:
code-excerpt "animate5/lib/main.dart (ShakeCurve)" plaster="none"?
```dart
import 'dart:math';
class ShakeCurve extends Curve {
  @override
  double transform(double t) => sin(t * pi * 2);
}
```
Browse the [Curves] documentation for a complete listing
(with visual previews) of the Curves constants that ship with Flutter.
:::
CurvedAnimation and AnimationController (described in the next section)
are both of type Animation<double>, so you can pass them interchangeably.
The CurvedAnimation wraps the object it's modifying—you
don't subclass AnimationController to implement a curve.
