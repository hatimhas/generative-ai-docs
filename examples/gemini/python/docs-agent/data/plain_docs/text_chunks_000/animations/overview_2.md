Animations also provide an AnimationStatus,
which indicates how the animation will evolve over time.
Whenever the animation's status changes,
the animation notifies all the listeners added with
addStatusListener. Typically, animations start
out in the dismissed status, which means they're
at the beginning of their range. For example,
animations that progress from 0.0 to 1.0
will be dismissed when their value is 0.0.
An animation might then run forward (from 0.0 to 1.0)
or perhaps in reverse (from 1.0 to 0.0).
Eventually, if the animation reaches the end of its range
(1.0), the animation reaches the completed status.
