code-excerpt path-base="layout/constraints/"?

:::note
If you are experiencing specific layout errors,
you might check out Common Flutter errors.
:::
When someone learning Flutter asks you why some widget
with width: 100 isn't 100 pixels wide,
the default answer is to tell them to put that widget
inside of a Center, right?
Don't do that.
If you do, they'll come back again and again,
asking why some FittedBox isn't working,
why that Column is overflowing, or what
IntrinsicWidth is supposed to be doing.
Instead, first tell them that Flutter layout is very different
from HTML layout (which is probably where they're coming from),
and then make them memorize the following rule:

Constraints go down. Sizes go up. Parent sets position.

Flutter layout can't really be understood without knowing
this rule, so Flutter developers should learn it early on.
In more detail:

A widget gets its own constraints from its parent.
  A constraint is just a set of 4 doubles:
  a minimum and maximum width, and a minimum and maximum height.
Then the widget goes through its own list of children.
  One by one, the widget tells its children what their
  constraints are (which can be different for each child),
  and then asks each child what size it wants to be.
Then, the widget positions its children
  (horizontally in the x axis, and vertically in the y axis),
  one by one.
And, finally, the widget tells its parent about its own size
  (within the original constraints, of course).

For example, if a composed widget contains a column
with some padding, and wants to lay out its two children
as follows:

The negotiation goes something like this:
Widget: "Hey parent, what are my constraints?"
Parent: "You must be from 0 to 300 pixels wide,
   and 0 to 85 tall."
Widget: "Hmmm, since I want to have 5 pixels of padding,
   then my children can have at most 290 pixels of width
   and 75 pixels of height."
Widget: "Hey first child, You must be from 0 to 290
   pixels wide, and 0 to 75 tall."
First child: "OK, then I wish to be 290 pixels wide,
   and 20 pixels tall."
Widget: "Hmmm, since I want to put my second child below the
   first one, this leaves only 55 pixels of height for
   my second child."
Widget: "Hey second child, You must be from 0 to 290 wide,
   and 0 to 55 tall."
Second child: "OK, I wish to be 140 pixels wide,
   and 30 pixels tall."
Widget: "Very well. My first child has position x: 5 and y: 5,
   and my second child has x: 80 and y: 25."
Widget: "Hey parent, I've decided that my size is going to be 300
   pixels wide, and 60 pixels tall."
Flutter's layout engine is designed to be a one-pass process.
This means that Flutter lays out its widgets very efficiently,
but does result in a few limitations:


A widget can decide its own size only within the
  constraints given to it by its parent.
  This means a widget usually
  can't have any size it wants.


A widget can't know and doesn't decide its own position
  in the screen, since it's the widget's parent who decides
  the position of the widget.


Since the parent's size and position, in its turn,
  also depends on its own parent, it's impossible to
  precisely define the size and position of any widget
  without taking into consideration the tree as a whole.


If a child wants a different size from its parent and
  the parent doesn't have enough information to align it,
  then the child's size might be ignored.
  Be specific when defining alignment.


In Flutter, widgets are rendered by their underlying
RenderBox objects. Many boxes in Flutter,
especially those that just take a single child,
pass their constraint on to their children.
Generally, there are three kinds of boxes,
in terms of how they handle their constraints:

Those that try to be as big as possible.
  For example, the boxes used by Center and
  ListView.
Those that try to be the same size as their children.
  For example, the boxes used by Transform and
  Opacity.
Those that try to be a particular size.
  For example, the boxes used by Image and
  Text.

Some widgets, for example Container,
vary from type to type based on their constructor arguments.
The Container constructor defaults
to trying to be as big as possible, but if you give it a width,
for instance, it tries to honor that and be that particular size.
Others, for example Row and Column (flex boxes)
vary based on the constraints they are given,
as described in the Flex section.
