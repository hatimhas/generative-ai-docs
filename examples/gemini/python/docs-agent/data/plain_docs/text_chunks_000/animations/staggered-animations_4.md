The stateful widget, StaggerDemo, creates the AnimationController
(the one who rules them all), specifying a 2000 ms duration. It plays
the animation, and builds the non-animating portion of the widget tree.
The animation begins when a tap is detected in the screen.
The animation runs forward, then backward.
```dart
[!class StaggerDemo extends StatefulWidget!] {
  @override
  State createState() => _StaggerDemoState();
}
class _StaggerDemoState extends State
    with TickerProviderStateMixin {
  late AnimationController _controller;
@override
  void initState() {
    super.initState();
_controller = AnimationController(
  duration: const Duration(milliseconds: 2000),
  vsync: this,
);

}
// ...Boilerplate...
[!Future _playAnimation() async!] {
    try {
      [!await _controller.forward().orCancel;!]
      [!await _controller.reverse().orCancel;!]
    } on TickerCanceled {
      // The animation got canceled, probably because it was disposed of.
    }
  }
@override
  [!Widget build(BuildContext context)!] {
    timeDilation = 10.0; // 1.0 is normal animation speed.
    return Scaffold(
      appBar: AppBar(
        title: const Text('Staggered Animation'),
      ),
      body: GestureDetector(
        behavior: HitTestBehavior.opaque,
        onTap: () {
          _playAnimation();
        },
        child: Center(
          child: Container(
            width: 300,
            height: 300,
            decoration: BoxDecoration(
              color: Colors.black.withOpacity(0.1),
              border: Border.all(
                color:  Colors.black.withOpacity(0.5),
              ),
            ),
            child: StaggerAnimation(controller:_controller.view),
          ),
        ),
      ),
    );
  }
}
```
