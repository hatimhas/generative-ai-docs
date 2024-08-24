:::note
You might be directed here if the framework
detects a problem involving box constraints.
The Flex section below might also apply.
:::
In certain situations,
a box's constraint is unbounded, or infinite.
This means that either the maximum width or
the maximum height is set to double.infinity.
A box that tries to be as big as possible won't
function usefully when given an unbounded constraint and,
in debug mode, throws an exception.
The most common case where a render box ends up
with an unbounded constraint is within a flex box
(Row or Column),
and within a scrollable region
(such as ListView and other ScrollView subclasses).
ListView, for example,
tries to expand to fit the space available
in its cross-direction
(perhaps it's a vertically-scrolling block and
tries to be as wide as its parent).
If you nest a vertically scrolling ListView
inside a horizontally scrolling ListView,
the inner list tries to be as wide as possible,
which is infinitely wide,
since the outer one is scrollable in that direction.
The next section describes the error you might
encounter with unbounded constraints in a Flex widget.
