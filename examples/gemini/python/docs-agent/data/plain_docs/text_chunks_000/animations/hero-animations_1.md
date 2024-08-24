Tapping any of the circular images flies that image to a new route
that displays it with a square shape.
Tapping the square image flies the hero back to
the original route, displayed with a circular shape.
Before moving to the sections specific to
standard
or radial hero animations,
read basic structure of a hero animation
to learn how to structure hero animation code,
and behind the scenes to understand
how Flutter performs a hero animation.
:::secondary What's the point?
* Use two hero widgets in different routes but with matching tags to
    implement the animation.
* The Navigator manages a stack containing the app's routes.
* Pushing a route on or popping a route from the Navigator's stack
    triggers the animation.
* The Flutter framework calculates a rectangle tween,
    RectTween that defines the hero's boundary
    as it flies from the source to the destination route.
    During its flight, the hero is moved to
    an application overlay, so that it appears on top of both routes.
:::
:::tip Terminology
If the concept of tweens or tweening is new to you,
check out the Animations in Flutter tutorial.
:::
Hero animations are implemented using two Hero
widgets: one describing the widget in the source route,
and another describing the widget in the destination route.
From the user's point of view, the hero appears to be shared, and
only the programmer needs to understand this implementation detail.
Hero animation code has the following structure:
Define a starting Hero widget, referred to as the source
   hero. The hero specifies its graphical representation
   (typically an image), and an identifying tag, and is in
   the currently displayed widget tree as defined by the source route.
Define an ending Hero widget, referred to as the destination hero.
   This hero also specifies its graphical representation,
   and the same tag as the source hero.
   It's essential that both hero widgets are created with
   the same tag, typically an object that represents the
   underlying data. For best results, the heroes should have
   virtually identical widget trees.
Create a route that contains the destination hero.
   The destination route defines the widget tree that exists
   at the end of the animation.
Trigger the animation by pushing the destination route on the
   Navigator's stack. The Navigator push and pop operations trigger
   a hero animation for each pair of heroes with matching tags in
   the source and destination routes.
Flutter calculates the tween that animates the Hero's bounds from
the starting point to the endpoint (interpolating size and position),
and performs the animation in an overlay.
The next section describes Flutter's process in greater detail.
