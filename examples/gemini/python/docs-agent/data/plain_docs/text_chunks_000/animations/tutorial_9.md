:::secondary What's the point?
* How to use the AnimatedWidget helper class
  (instead of addListener()
  and setState()) to create a widget that animates.
* Use AnimatedWidget to create a widget that performs
  a reusable animation.
  To separate the transition from the widget, use an
  AnimatedBuilder, as shown in the
  Refactoring with AnimatedBuilder section.
* Examples of AnimatedWidgets in the Flutter API:
  AnimatedBuilder, AnimatedModalBarrier,
  DecoratedBoxTransition, FadeTransition,
  PositionedTransition, RelativePositionedTransition,
  RotationTransition, ScaleTransition,
  SizeTransition, SlideTransition.
:::
The AnimatedWidget base class allows you to separate out
the core widget code from the animation code.
AnimatedWidget doesn't need to maintain a State
object to hold the animation. Add the following AnimatedLogo class:
code-excerpt path-base="animation/animate2"?
code-excerpt "lib/main.dart (AnimatedLogo)"?
```dart
class AnimatedLogo extends AnimatedWidget {
  const AnimatedLogo()
      : super(listenable: animation);
@override
  Widget build(BuildContext context) {
    final animation = listenable as Animation;
    return Center(
      child: Container(
        margin: const EdgeInsets.symmetric(vertical: 10),
        height: animation.value,
        width: animation.value,
        child: const FlutterLogo(),
      ),
    );
  }
}
```
code-excerpt path-base="animation"?
AnimatedLogo uses the current value of the animation
when drawing itself.
The LogoApp still manages the AnimationController and the Tween,
and it passes the Animation object to AnimatedLogo:
```dart diff
  void main() => runApp(const LogoApp());

class AnimatedLogo extends AnimatedWidget {
const AnimatedLogo()
: super(listenable: animation);

@override
Widget build(BuildContext context) {
final animation = listenable as Animation;
return Center(
child: Container(
margin: const EdgeInsets.symmetric(vertical: 10),
height: animation.value,
width: animation.value,
child: const FlutterLogo(),
),
);
}
}

class LogoApp extends StatefulWidget {
    // ...
@override
void initState() {
  super.initState();
  controller =
      AnimationController(duration: const Duration(seconds: 2), vsync: this);
-     animation = Tween(begin: 0, end: 300).animate(controller)
-       ..addListener(() {
-         setState(() {
-           // The state that has changed here is the animation object's value.
-         });
-       });
+     animation = Tween(begin: 0, end: 300).animate(controller);
  controller.forward();
}
@override
-   Widget build(BuildContext context) {
-     return Center(
-       child: Container(
-         margin: const EdgeInsets.symmetric(vertical: 10),
-         height: animation.value,
-         width: animation.value,
-         child: const FlutterLogo(),
-       ),
-     );
-   }
+   Widget build(BuildContext context) => AnimatedLogo(animation: animation);
// ...
  }
```


App source: animate2
