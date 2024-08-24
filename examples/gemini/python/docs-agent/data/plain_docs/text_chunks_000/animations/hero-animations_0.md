:::secondary What you'll learn
* The hero refers to the widget that flies between screens.
* Create a hero animation using Flutter's Hero widget.
* Fly the hero from one screen to another.
* Animate the transformation of a hero's shape from circular to
    rectangular while flying it from one screen to another.
* The Hero widget in Flutter implements a style of animation
    commonly known as shared element transitions or
    shared element animations.
:::
You've probably seen hero animations many times. For example, a screen displays
a list of thumbnails representing items for sale.  Selecting an item flies it to
a new screen, containing more details and a "Buy" button. Flying an image from
one screen to another is called a hero animation in Flutter, though the same
motion is sometimes referred to as a shared element transition.
You might want to watch this one-minute video introducing the Hero widget:
This guide demonstrates how to build standard hero animations, and hero
animations that transform the image from a circular shape to a square shape
during flight.
:::secondary Examples
This guide provides examples of each hero animation style at
the following links.
Standard hero animation code
Radial hero animation code
::
:::secondary New to Flutter?
This page assumes you know how to create a layout
using Flutter's widgets. For more information, see
Building Layouts in Flutter.
:::
:::tip Terminology
  A Route describes a page or screen in a Flutter app.
:::
You can create this animation in Flutter with Hero widgets.
As the hero animates from the source to the destination route,
the destination route (minus the hero) fades into view.
Typically, heroes are small parts of the UI, like images,
that both routes have in common. From the user's perspective
the hero "flies" between the routes. This guide shows how
to create the following hero animations:
Standard hero animations
A standard hero animation flies the hero from one route to a new route,
usually landing at a different location and with a different size.
The following video (recorded at slow speed) shows a typical example.
Tapping the flippers in the center of the route flies them to the
upper left corner of a new, blue route, at a smaller size.
Tapping the flippers in the blue route (or using the device's
back-to-previous-route gesture) flies the flippers back to
the original route.
Radial hero animations
In radial hero animation, as the hero flies between routes
its shape appears to change from circular to rectangular.
The following video (recorded at slow speed),
shows an example of a radial hero animation. At the start, a
row of three circular images appears at the bottom of the route.
