In the stateless widget, StaggerAnimation,
the build() function instantiates an
AnimatedBuilder—a general purpose widget for building
animations. The AnimatedBuilder
builds a widget and configures it using the Tweens' current values.
The example creates a function named _buildAnimation() (which performs
the actual UI updates), and assigns it to its builder property.
AnimatedBuilder listens to notifications from the animation controller,
marking the widget tree dirty as values change.
For each tick of the animation, the values are updated,
resulting in a call to _buildAnimation().
```dart
[!class StaggerAnimation extends StatelessWidget!] {
  StaggerAnimation() :
// Each animation defined here transforms its value during the subset
// of the controller's duration defined by the animation's interval.
// For example the opacity animation transforms its value during
// the first 10% of the controller's duration.

[!opacity = Tween<double>!](
  begin: 0.0,
  end: 1.0,
).animate(
  CurvedAnimation(
    parent: controller,
    curve: const Interval(
      0.0,
      0.100,
      curve: Curves.ease,
    ),
  ),
),

// ... Other tween definitions ...
);

[!final AnimationController controller;!]
  [!final Animation opacity;!]
  [!final Animation width;!]
  [!final Animation height;!]
  [!final Animation padding;!]
  [!final Animation borderRadius;!]
  [!final Animation color;!]
// This function is called each time the controller "ticks" a new frame.
  // When it runs, all of the animation's values will have been
  // updated to reflect the controller's current value.
  [!Widget _buildAnimation(BuildContext context, Widget? child)!] {
    return Container(
      padding: padding.value,
      alignment: Alignment.bottomCenter,
      child: Opacity(
        opacity: opacity.value,
        child: Container(
          width: width.value,
          height: height.value,
          decoration: BoxDecoration(
            color: color.value,
            border: Border.all(
              color: Colors.indigo[300]!,
              width: 3,
            ),
            borderRadius: borderRadius.value,
          ),
        ),
      ),
    );
  }
@override
  [!Widget build(BuildContext context)!] {
    return !AnimatedBuilder!;
  }
}
```
