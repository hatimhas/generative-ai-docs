}/tree/}/examples 
code-excerpt path-base="animation"?
:::secondary What you'll learn
* How to use the fundamental classes from the
  animation library to add animation to a widget.
* When to use AnimatedWidget vs. AnimatedBuilder.
:::
This tutorial shows you how to build explicit animations in Flutter.
After introducing some of the essential concepts, classes,
and methods in the animation library, it walks you through 5
animation examples. The examples build on each other,
introducing you to different aspects of the animation library.
The Flutter SDK also provides built-in explicit animations,
such as FadeTransition, SizeTransition,
and SlideTransition. These simple animations are
triggered by setting a beginning and ending point.
They are simpler to implement
than custom explicit animations, which are described here.

:::secondary What's the point?
* Animation, a core class in Flutter's animation library,
  interpolates the values used to guide an animation.
* An Animation object knows the current state of an animation
  (for example, whether it's started, stopped,
  or moving forward or in reverse),
  but doesn't know anything about what appears onscreen.
* An AnimationController manages the Animation.
* A CurvedAnimation defines progression as a non-linear curve.
* A Tween interpolates between the range of data as used by the
  object being animated.
  For example, a Tween might define an interpolation
  from red to blue, or from 0 to 255.
* Use Listeners and StatusListeners to monitor
  animation state changes.
:::
The animation system in Flutter is based on typed
Animation objects. Widgets can either incorporate
these animations in their build functions directly by
reading their current value and listening to their state
changes or they can use the animations as the basis of
more elaborate animations that they pass along to
other widgets.
