The following diagram shows the clipped image at the beginning
(t = 0.0), and the end (t = 1.0) of the animation.

The blue gradient (representing the image), indicates where the clip
shapes intersect. At the beginning of the transition,
the result of the intersection is a circular clip (ClipOval).
During the transformation, the ClipOval scales from minRadius
to maxRadius while the ClipRect maintains a constant size.
At the end of the transition the intersection of the circular and
rectangular clips yield a rectangle that's the same size as the hero
widget. In other words, at the end of the transition the image is no
longer clipped.
Create a new Flutter example and
update it using the files from the
radial_hero_animation GitHub directory.
To run the example:

Tap on one of the three circular thumbnails to animate the image
  to a larger square positioned in the middle of a new route that
  obscures the original route.
Return to the previous route by tapping the image, or by using the
  device's back-to-the-previous-route gesture.
You can slow the transition further using the timeDilation
  property.
