Like all interactive widgets, the complete animation consists
of a widget pair: a stateless and a stateful widget.
The stateless widget specifies the Tweens,
defines the Animation objects, and provides a build() function
responsible for building the animating portion of the widget tree.
The stateful widget creates the controller, plays the animation,
and builds the non-animating portion of the widget tree.
The animation begins when a tap is detected anywhere in the screen.
Full code for basic_staggered_animation's main.dart
