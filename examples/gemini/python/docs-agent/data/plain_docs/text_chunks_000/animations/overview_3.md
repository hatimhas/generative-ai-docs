To create an animation, first create an AnimationController.
As well as being an animation itself, an AnimationController
lets you control the animation. For example,
you can tell the controller to play the animation
forward or stop the animation.
You can also fling animations,
which uses a physical simulation, such as a spring,
to drive the animation.
Once you've created an animation controller,
you can start building other animations based on it.
For example, you can create a ReverseAnimation
that mirrors the original animation but runs in the
opposite direction (from 1.0 to 0.0).
Similarly, you can create a CurvedAnimation
whose value is adjusted by a Curve.
