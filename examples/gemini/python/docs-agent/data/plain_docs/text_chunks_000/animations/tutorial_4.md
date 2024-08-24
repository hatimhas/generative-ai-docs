By default, the AnimationController object ranges from 0.0 to 1.0.
If you need a different range or a different data type, you can use a
Tween to configure an animation to interpolate to a
different range or data type. For example, the
following Tween goes from -200.0 to 0.0:
code-excerpt "animate5/lib/main.dart (tween)"?
dart
tween = Tween<double>(begin: -200, end: 0);
A Tween is a stateless object that takes only begin and end.
The sole job of a Tween is to define a mapping from an
input range to an output range. The input range is commonly
0.0 to 1.0, but that's not a requirement.
A Tween inherits from Animatable<T>, not from Animation<T>.
An Animatable, like Animation, doesn't have to output double.
For example, ColorTween specifies a progression between two colors.
code-excerpt "animate5/lib/main.dart (colorTween)"?
dart
colorTween = ColorTween(begin: Colors.transparent, end: Colors.black54);
A Tween object doesn't store any state. Instead, it provides the
evaluate(Animation<double> animation) method that uses the 
transform function to map the current value of the animation
(between 0.0 and 1.0), to the actual animation value. 
The current value of the Animation object can be found in the
.value method. The evaluate function also performs some housekeeping,
such as ensuring that begin and end are returned when the
animation values are 0.0 and 1.0, respectively.
