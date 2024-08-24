:::secondary What's the point?
* A radial transformation animates a circular shape into a square
    shape.
* A radial hero animation performs a radial transformation while
    flying the hero from the source route to the destination route.
* MaterialRectCenter­Arc­Tween defines the tween animation.
* Build the destination route using PageRouteBuilder.
:::
Flying a hero from one route to another as it transforms
from a circular shape to a rectangular shape is a slick
effect that you can implement using Hero widgets.
To accomplish this, the code animates the intersection of
two clip shapes: a circle and a square.
Throughout the animation, the circle clip (and the image)
scales from minRadius to maxRadius, while the square
clip maintains constant size. At the same time,
the image flies from its position in the source route to its
position in the destination route. For visual examples
of this transition, see Radial transformation
in the Material motion spec.
This animation might seem complex (and it is), but you can customize the
provided example to your needs. The heavy lifting is done for you.

:::secondary Radial hero animation code
Each of the following examples demonstrates a radial hero animation.
This guide describes the first example.
radial_hero_animation
: A radial hero animation as described in the Material motion spec.
basic_radial_hero_animation
: The simplest example of a radial hero animation. The destination
  route has no Scaffold, Card, Column, or Text.
  This basic example, provided for your reference, isn't
  described in this guide.
radial_hero_animation_animate_rectclip
: Extends radial_hero_animation by also animating the size of the
  rectangular clip. This more advanced example,
  provided for your reference, isn't described in this guide.
:::
:::tip Pro tip
The radial hero animation involves intersecting a round shape with
a square shape. This can be hard to see, even when slowing
the animation with timeDilation, so you might consider enabling
the debugPaintSizeEnabled flag during development.
:::
