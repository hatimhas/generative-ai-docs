A loose constraint is one that has a minimum
of zero and a maximum non-zero.
Some boxes loosen the incoming constraints,
meaning the maximum is maintained but the
minimum is removed, so the widget can have
a minimum width and height both equal to zero.
Ultimately, Center's purpose is to transform
the tight constraints it received from its parent
(the screen) to loose constraints for its child
(the Container).
If you revisit Example 3,
the Center allows the red Container to be smaller,
but not bigger than the screen.
