The Tween<T> abstract class maps a double
value nominally in the range 0.0-1.0 to a typed value
(for example, a Color, or another double).
It is an Animatable.
It has a notion of an output type (T),
a begin value and an end value of that type,
and a way to interpolate (lerp) between the begin
and end values for a given input value (the double nominally in
the range 0.0-1.0).
Tween classes are stateless and immutable.
