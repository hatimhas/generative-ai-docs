:::secondary What's the point?
* Use addStatusListener() for notifications of changes
  to the animation's state, such as starting, stopping,
  or reversing direction.
* Run an animation in an infinite loop by reversing direction when
  the animation has either completed or returned to its starting state.
:::
It's often helpful to know when an animation changes state,
such as finishing, moving forward, or reversing.
You can get notifications for this with addStatusListener().
The following code modifies the previous example so that
it listens for a state change and prints an update.
The highlighted line shows the change:
code-excerpt "animate3/lib/main.dart (print-state)" plaster="none" replace="/\/\/ (\.\..*)/$1;/g; /\n  }/$&\n  \/\/ .../g"?
```dart highlightLines=11
class _LogoAppState extends State with SingleTickerProviderStateMixin {
  late Animation animation;
  late AnimationController controller;
@override
  void initState() {
    super.initState();
    controller =
        AnimationController(duration: const Duration(seconds: 2), vsync: this);
    animation = Tween(begin: 0, end: 300).animate(controller)
      ..addStatusListener((status) => print('$status'));
    controller.forward();
  }
  // ...
}
```
Running this code produces this output:
console
AnimationStatus.forward
AnimationStatus.completed
Next, use addStatusListener() to reverse the animation
at the beginning or the end. This creates a "breathing" effect:
dart diff
  void initState() {
    super.initState();
    controller =
        AnimationController(duration: const Duration(seconds: 2), vsync: this);
-   animation = Tween<double>(begin: 0, end: 300).animate(controller);
+   animation = Tween<double>(begin: 0, end: 300).animate(controller)
+     ..addStatusListener((status) {
+       if (status == AnimationStatus.completed) {
+         controller.reverse();
+       } else if (status == AnimationStatus.dismissed) {
+         controller.forward();
+       }
+     })
+     ..addStatusListener((status) => print('$status'));
    controller.forward();
  }
App source: animate3
