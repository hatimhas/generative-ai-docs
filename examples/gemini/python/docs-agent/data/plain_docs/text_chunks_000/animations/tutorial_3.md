AnimationController is a special Animation
object that generates a new value whenever the hardware
is ready for a new frame. By default,
an AnimationController linearly produces the numbers
from 0.0 to 1.0 during a given duration.
For example, this code creates an Animation object,
but does not start it running:
code-excerpt "animate5/lib/main.dart (animation-controller)"?
dart
controller =
    AnimationController(duration: const Duration(seconds: 2), vsync: this);
AnimationController derives from Animation<double>, so it can be used
wherever an Animation object is needed. However, the AnimationController
has additional methods to control the animation. For example, you start
an animation with the .forward() method. The generation of numbers is
tied to the screen refresh, so typically 60 numbers are generated per
second. After each number is generated, each Animation object calls the
attached Listener objects. To create a custom display list for each
child, see RepaintBoundary.
When creating an AnimationController, you pass it a vsync argument.
The presence of vsync prevents offscreen animations from consuming
unnecessary resources.
You can use your stateful object as the vsync by adding
SingleTickerProviderStateMixin to the class definition.
You can see an example of this in animate1 on GitHub.

The vsync object ties the ticking of the animation controller to
the visibility of the widget, so that when the animating widget goes
off-screen, the ticking stops, and when the widget is restored, it
starts again (without stopping the clock, so it's as if it had
been ticking the whole time, but without using the CPU.)
To use your custom State object as the vsync, include the
TickerProviderStateMixin when defining the custom State class.

:::note
In some cases, a position might exceed the AnimationController's
0.0-1.0 range. For example, the fling() function
allows you to provide velocity, force, and position
(via the Force object). The position can be anything and
so can be outside of the 0.0 to 1.0 range.
A CurvedAnimation can also exceed the 0.0 to 1.0 range,
even if the AnimationController doesn't.
Depending on the curve selected, the output of
the CurvedAnimation can have a wider range than the input.
For example, elastic curves such as Curves.elasticIn
significantly overshoots or undershoots the default range.
:::
