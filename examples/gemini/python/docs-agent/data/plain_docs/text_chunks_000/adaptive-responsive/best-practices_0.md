Recommended best practices for adaptive design include:
Break down your widgets
While designing your app, try to break down large,
complex widgets into smaller, simpler ones.
Refactoring widgets can reduce the complexity of
adopting an adaptive UI by sharing core pieces of code.
There are other benefits as well:

On the performance side, having lots of small const
  widgets improves rebuild times over having large,
  complex widgets.
Flutter can reuse const widget instances,
  while a larger complex widget has to be set up
  for every rebuild.
From a code health perspective, organizing your UI
  into smaller bite sized pieces helps keep the complexity
  of each Widget down. A less-complex Widget is more readable,
  easier to refactor, and less likely to have surprising behavior.

To learn more, check out the 3 steps of
adaptive design in General approach.
