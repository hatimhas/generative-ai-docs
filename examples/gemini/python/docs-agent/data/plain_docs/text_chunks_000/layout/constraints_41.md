A flex box (Row and Column) behaves
differently depending on whether its
constraint is bounded or unbounded in
its primary direction.
A flex box with a bounded constraint in its
primary direction tries to be as big as possible.
A flex box with an unbounded constraint
in its primary direction tries to fit its children
in that space. Each child's flex value must be
set to zero, meaning that you can't use
Expanded when the flex box is inside
another flex box or a scrollable;
otherwise it throws an exception.
The cross direction
(width for Column or height for Row),
must never be unbounded,
or it can't reasonably align its children.
