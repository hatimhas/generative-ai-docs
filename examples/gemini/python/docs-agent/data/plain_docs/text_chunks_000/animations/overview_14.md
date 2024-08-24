The AnimationController is a stateful
Animation<double> that uses a Ticker to give itself life.
It can be started and stopped. At each tick, it takes the time
elapsed since it was started and passes it to a Simulation to obtain
a value. That is then the value it reports. If the Simulation
reports that at that time it has ended, then the controller stops
itself.
The animation controller can be given a lower and upper bound to
animate between, and a duration.
In the simple case (using forward() or reverse()), the animation controller simply does a linear
interpolation from the lower bound to the upper bound (or vice versa,
for the reverse direction) over the given duration.
When using repeat(), the animation controller uses a linear
interpolation between the given bounds over the given duration, but
does not stop.
When using animateTo(), the animation controller does a linear
interpolation over the given duration from the current value to the
given target. If no duration is given to the method, the default
duration of the controller and the range described by the controller's
lower bound and upper bound is used to determine the velocity of the
animation.
When using fling(), a Force is used to create a specific
simulation which is then used to drive the controller.
When using animateWith(), the given simulation is used to drive the
controller.
These methods all return the future that the Ticker provides and
which will resolve when the controller next stops or changes
simulation.
