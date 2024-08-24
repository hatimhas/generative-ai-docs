:::secondary What's the point?
* Specify a route using MaterialPageRoute, CupertinoPageRoute,
    or build a custom route using PageRouteBuilder.
    The examples in this section use MaterialPageRoute.
* Change the size of the image at the end of the transition by
    wrapping the destination's image in a SizedBox.
* Change the location of the image by placing the destination's
    image in a layout widget. These examples use Container.
:::

:::secondary Standard hero animation code
Each of the following examples demonstrates flying an image from one
route to another. This guide describes the first example.
hero_animation
: Encapsulates the hero code in a custom PhotoHero widget.
  Animates the hero's motion along a curved path,
  as described in the Material motion spec.
basic_hero_animation
: Uses the hero widget directly.
  This more basic example, provided for your reference, isn't
  described in this guide.
:::
