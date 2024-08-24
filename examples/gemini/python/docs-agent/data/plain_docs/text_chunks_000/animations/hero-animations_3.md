The examples in this guide use the following classes to
implement hero animations:
Hero
: The widget that flies from the source to the destination route.
  Define one Hero for the source route and another for the
  destination route, and assign each the same tag.
  Flutter animates pairs of heroes with matching tags.
InkWell
: Specifies what happens when tapping the hero.
  The InkWell's onTap() method builds the
  new route and pushes it to the Navigator's stack.
Navigator
: The Navigator manages a stack of routes. Pushing a route on or
  popping a route from the Navigator's stack triggers the animation.
Route
: Specifies a screen or page. Most apps,
  beyond the most basic, have multiple routes.
