To animate beyond the 0.0 to 1.0 interval, you can use a
Tween<T>, which interpolates between its
begin and end values. Many types have specific
Tween subclasses that provide type-specific interpolation.
For example, ColorTween interpolates between colors and
RectTween interpolates between rects.
You can define your own interpolations by creating
your own subclass of Tween and overriding its
lerp function.
By itself, a tween just defines how to interpolate
between two values. To get a concrete value for the
current frame of an animation, you also need an
animation to determine the current state.
There are two ways to combine a tween
with an animation to get a concrete value:


You can evaluate the tween at the current
   value of an animation. This approach is most useful
   for widgets that are already listening to the animation and hence
   rebuilding whenever the animation changes value.


You can animate the tween based on the animation.
   Rather than returning a single value, the animate function
   returns a new Animation that incorporates the tween.
   This approach is most useful when you want to give the
   newly created animation to another widget,
   which can then read the current value that incorporates
   the tween as well as listen for changes to the value.
