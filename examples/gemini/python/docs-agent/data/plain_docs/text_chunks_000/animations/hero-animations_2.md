The following describes how Flutter performs the
transition from one route to another.

Before transition, the source hero waits in the source
route's widget tree. The destination route does not yet exist,
and the overlay is empty.


Pushing a route to the Navigator triggers the animation.
At t=0.0, Flutter does the following:


Calculates the destination hero's path, offscreen,
  using the curved motion as described in the Material
  motion spec. Flutter now knows where the hero ends up.


Places the destination hero in the overlay,
  at the same location and size as the source hero.
  Adding a hero to the overlay changes its Z-order so that it
  appears on top of all routes.


Moves the source hero offscreen.




As the hero flies, its rectangular bounds are animated using
Tween<Rect>, specified in Hero's
createRectTween property.
By default, Flutter uses an instance of
MaterialRectArcTween, which animates the
rectangle's opposing corners along a curved path.
(See Radial hero animations for an example
that uses a different Tween animation.)


When the flight completes:


Flutter moves the hero widget from the overlay to
  the destination route. The overlay is now empty.


The destination hero appears in its final position
  in the destination route.


The source hero is restored to its route.



Popping the route performs the same process,
animating the hero back to its size
and location in the source route.
