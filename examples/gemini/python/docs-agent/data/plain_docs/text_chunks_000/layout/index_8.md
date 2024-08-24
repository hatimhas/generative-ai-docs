code-excerpt path-base=""?
One of the most common layout patterns is to arrange
widgets vertically or horizontally. You can use a
Row widget to arrange widgets horizontally,
and a Column widget to arrange widgets vertically.
:::secondary What's the point?
* Row and Column are two of the most commonly used layout patterns.
* Row and Column each take a list of child widgets.
* A child widget can itself be a Row, Column,
    or other complex widget.
* You can specify how a Row or Column aligns its children,
    both vertically and horizontally.
* You can stretch or constrain specific child widgets.
* You can specify how child widgets use the Row's or
    Column's available space.
:::
To create a row or column in Flutter, you add a list of children
widgets to a Row or Column widget. In turn,
each child can itself be a row or column, and so on.
The following example shows how it is possible to nest rows or
columns inside of rows or columns.
This layout is organized as a Row. The row contains two children:
a column on the left, and an image on the right:

The left column's widget tree nests rows and columns.

You'll implement some of Pavlova's layout code in
Nesting rows and columns.
:::note
Row and Column are basic primitive widgets for horizontal
and vertical layouts—these low-level widgets allow for maximum
customization. Flutter also offers specialized, higher level widgets
that might be sufficient for your needs. For example,
instead of Row you might prefer ListTile,
an easy-to-use widget with properties for leading and trailing icons,
and up to 3 lines of text.  Instead of Column, you might prefer
ListView, a column-like layout that automatically scrolls
if its content is too long to fit the available space.
For more information, see Common layout widgets.
:::
