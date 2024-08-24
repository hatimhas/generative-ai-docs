The Animation abstract class provides a
value of a given type, a concept of animation
direction and animation status, and a listener interface to
register callbacks that get invoked when the value or status change.
Some subclasses of Animation have values that never change
(kAlwaysCompleteAnimation, kAlwaysDismissedAnimation,
AlwaysStoppedAnimation); registering callbacks on
these has no effect as the callbacks are never called.
The Animation<double> variant is special because it can be used to
represent a double nominally in the range 0.0-1.0, which is the input
expected by Curve and Tween classes, as well as some further
subclasses of Animation.
Some Animation subclasses are stateless,
merely forwarding listeners to their parents.
Some are very stateful.
