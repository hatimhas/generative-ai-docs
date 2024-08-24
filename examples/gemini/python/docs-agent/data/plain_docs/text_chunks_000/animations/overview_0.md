The animation system in Flutter is based on typed
Animation objects. Widgets can either
incorporate these animations in their build
functions directly by reading their current value and listening to their
state changes or they can use the animations as the basis of more elaborate
animations that they pass along to other widgets.
The primary building block of the animation system is the
Animation class. An animation represents a value
of a specific type that can change over the lifetime of
the animation. Most widgets that perform an animation
receive an Animation object as a parameter,
from which they read the current value of the animation
and to which they listen for changes to that value.
