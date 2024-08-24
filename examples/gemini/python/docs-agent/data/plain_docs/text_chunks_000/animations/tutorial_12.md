:::secondary What's the point?
* The Curves class defines an array of
  commonly used curves that you can
  use with a CurvedAnimation.
:::
In this section, you'll build on the example from
monitoring the progress of the animation
(animate3), which used AnimatedWidget
to animate in and out continuously. Consider the case
where you want to animate in and out while the
opacity animates from transparent to opaque.
:::note
This example shows how to use multiple tweens on the same animation
controller, where each tween manages a different effect in
the animation. It is for illustrative purposes only.
If you were tweening opacity and size in production code,
you'd probably use FadeTransition and SizeTransition
instead.
:::
Each tween manages an aspect of the animation. For example:
code-excerpt "animate5/lib/main.dart (tweens)" plaster="none"?
dart
controller =
    AnimationController(duration: const Duration(seconds: 2), vsync: this);
sizeAnimation = Tween<double>(begin: 0, end: 300).animate(controller);
opacityAnimation = Tween<double>(begin: 0.1, end: 1).animate(controller);
You can get the size with sizeAnimation.value and the opacity
with opacityAnimation.value, but the constructor for AnimatedWidget
only takes a single Animation object. To solve this problem,
the example creates its own Tween objects and explicitly calculates the
values.
Change AnimatedLogo to encapsulate its own Tween objects,
and its build() method calls Tween.evaluate()
on the parent's animation object to calculate
the required size and opacity values.
The following code shows the changes with highlights:
code-excerpt "animate5/lib/main.dart (diff)" replace="/(static final|child: Opacity|opacity:|_sizeTween\.|CurvedAnimation).*/[!$&!]/g"?
```dart
class AnimatedLogo extends AnimatedWidget {
  const AnimatedLogo()
      : super(listenable: animation);
// Make the Tweens static because they don't change.
  [!static final _opacityTween = Tween(begin: 0.1, end: 1);!]
  [!static final _sizeTween = Tween(begin: 0, end: 300);!]
@override
  Widget build(BuildContext context) {
    final animation = listenable as Animation;
    return Center(
      [!child: Opacity(!]
        [!opacity: _opacityTween.evaluate(animation),!]
        child: Container(
          margin: const EdgeInsets.symmetric(vertical: 10),
          height: [!_sizeTween.evaluate(animation),!]
          width: [!_sizeTween.evaluate(animation),!]
          child: const FlutterLogo(),
        ),
      ),
    );
  }
}
class LogoApp extends StatefulWidget {
  const LogoApp();
@override
  State createState() => _LogoAppState();
}
class _LogoAppState extends State with SingleTickerProviderStateMixin {
  late Animation animation;
  late AnimationController controller;
@override
  void initState() {
    super.initState();
    controller =
        AnimationController(duration: const Duration(seconds: 2), vsync: this);
    animation = [!CurvedAnimation(parent: controller, curve: Curves.easeIn)!]
      ..addStatusListener((status) {
        if (status == AnimationStatus.completed) {
          controller.reverse();
        } else if (status == AnimationStatus.dismissed) {
          controller.forward();
        }
      });
    controller.forward();
  }
@override
  Widget build(BuildContext context) => AnimatedLogo(animation: animation);
@override
  void dispose() {
    controller.dispose();
    super.dispose();
  }
}
```
App source: animate5
