In Flutter, an Animation object knows nothing about what
is onscreen. An Animation is an abstract class that
understands its current value and its state (completed or dismissed).
One of the more commonly used animation types is Animation<double>.
An Animation object sequentially generates
interpolated numbers between two values over a certain duration.
The output of an Animation object might be linear,
a curve, a step function, or any other mapping you can devise.
Depending on how the Animation object is controlled,
it could run in reverse, or even switch directions in the
middle.
Animations can also interpolate types other than double, such as
Animation<Color> or Animation<Size>.
An Animation object has state. Its current value is
always available in the .value member.
An Animation object knows nothing about rendering or
build() functions.
