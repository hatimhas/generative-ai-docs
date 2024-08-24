It's very common to hear that some constraint is
"tight" or "loose", so what does that mean?
Tight constraints
A tight constraint offers a single possibility,
an exact size. In other words, a tight constraint
has its maximum width equal to its minimum width;
and has its maximum height equal to its minimum height.
An example of this is the App widget,
which is contained by the RenderView class:
the box used by the child returned by the
application's build function is given a constraint
that forces it to exactly fill the application's content area
(typically, the entire screen).
Another example: if you nest a bunch of boxes inside
each other at the root of your application's render tree,
they'll all exactly fit in each other,
forced by the box's tight constraints.
If you go to Flutter's box.dart file and search for
the BoxConstraints constructors,
you'll find the following:
dart
BoxConstraints.tight(Size size)
   : minWidth = size.width,
     maxWidth = size.width,
     minHeight = size.height,
     maxHeight = size.height;
If you revisit Example 2,
the screen forces the red Container to be
exactly the same size as the screen.
The screen achieves that, of course, by passing tight
constraints to the Container.
