Another way to approach these situations is to
use the maxWidth property of BoxConstraints.
This involves the following:

Wrap the GridViewin a ConstrainedBox and give
  it a BoxConstraints with a maximum width set.
Use a Container instead of a ConstrainedBox
  if you want other functionality like setting the
  background color.

For choosing the maximum width value,
consider using the values recommended
by Material 3 in the Applying layout guide.
