Flying an image from one route to another is easy to implement
using Flutter's hero widget. When using MaterialPageRoute
to specify the new route, the image flies along a curved path,
as described by the Material Design motion spec.
Create a new Flutter example and
update it using the files from the hero_animation.
To run the example:

Tap on the home route's photo to fly the image to a new route
  showing the same photo at a different location and scale.
Return to the previous route by tapping the image, or by using the
  device's back-to-the-previous-route gesture.
You can slow the transition further using the timeDilation
  property.
