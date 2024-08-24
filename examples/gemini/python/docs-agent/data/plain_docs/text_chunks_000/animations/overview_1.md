Whenever the animation's value changes,
the animation notifies all the listeners added with
addListener. Typically, a State
object that listens to an animation calls
setState on itself in its listener callback
to notify the widget system that it needs to
rebuild with the new value of the animation.
This pattern is so common that there are two widgets
that help widgets rebuild when animations change value:
AnimatedWidget and AnimatedBuilder.
The first, AnimatedWidget, is most useful for
stateless animated widgets. To use AnimatedWidget,
simply subclass it and implement the build function.
The second, AnimatedBuilder, is useful for more complex widgets
that wish to include an animation as part of a larger build function.
To use AnimatedBuilder, simply construct the widget
and pass it a builder function.
