:::
The app is essentially animating a Container whose
decoration and size are animated. The Container
is within another Container whose padding moves the
inner container around and an Opacity widget that's
used to fade everything in and out.
The following diagram shows the Intervals used in the
basic_staggered_animation example.
You might notice the following characteristics:
The opacity changes during the first 10% of the timeline.
A tiny gap occurs between the change in opacity,
  and the change in width.
Nothing animates during the last 25% of the timeline.
Increasing the padding makes the widget appear to rise upward.
Increasing the border radius to 0.5,
  transforms the square with rounded corners into a circle.
The padding and height changes occur during
  the same exact interval, but they don't have to.
To set up the animation:
Create an AnimationController that manages all of the
  Animations.
Create a Tween for each property being animated.
The Tween defines a range of values.
The Tween's animate method requires the
    parent controller, and produces an Animation
    for that property.
Specify the interval on the Animation's curve property.
When the controlling animation's value changes,
the new animation's value changes, triggering the UI to update.
The following code creates a tween for the width property.
It builds a CurvedAnimation,
specifying an eased curve. See Curves for
other available pre-defined animation curves.
dart
width = Tween(
  begin: 50.0,
  end: 150.0,
).animate(
  CurvedAnimation(
    parent: controller,
    curve: const Interval(
      0.125,
      0.250,
      curve: Curves.ease,
    ),
  ),
),
The begin and end values don't have to be doubles.
The following code builds the tween for the borderRadius property
(which controls the roundness of the square's corners),
using BorderRadius.circular().
dart
borderRadius = BorderRadiusTween(
  begin: BorderRadius.circular(4),
  end: BorderRadius.circular(75),
).animate(
  CurvedAnimation(
    parent: controller,
    curve: const Interval(
      0.375,
      0.500,
      curve: Curves.ease,
    ),
  ),
),
