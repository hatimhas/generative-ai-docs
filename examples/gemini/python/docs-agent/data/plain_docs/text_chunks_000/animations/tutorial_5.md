To use a Tween object, call animate() on the Tween,
passing in the controller object. For example,
the following code generates the
integer values from 0 to 255 over the course of 500 ms.
code-excerpt "animate5/lib/main.dart (IntTween)"?
dart
AnimationController controller = AnimationController(
    duration: const Duration(milliseconds: 500), vsync: this);
Animation<int> alpha = IntTween(begin: 0, end: 255).animate(controller);
:::note
The animate() method returns an Animation,
not an Animatable.
:::
The following example shows a controller, a curve, and a Tween:
code-excerpt "animate5/lib/main.dart (IntTween-curve)"?
dart
AnimationController controller = AnimationController(
    duration: const Duration(milliseconds: 500), vsync: this);
final Animation<double> curve =
    CurvedAnimation(parent: controller, curve: Curves.easeOut);
Animation<int> alpha = IntTween(begin: 0, end: 255).animate(curve);
