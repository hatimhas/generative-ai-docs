Once an application has the ability to focus, the next thing many apps want to
do is to allow the user to control the focus using the keyboard or another input
device. The most common example of this is "tab traversal" where the user
presses Tab to go to the "next" control. Controlling what "next"
means is the subject of this section. This kind of traversal is provided by
Flutter by default.
In a simple grid layout, it's fairly easy to decide which control is next. If
you're not at the end of the row, then it's the one to the right (or left for
right-to-left locales). If you are at the end of a row, it's the first control
in the next row. Unfortunately, applications are rarely laid out in grids, so
more guidance is often needed.
The default algorithm in Flutter (ReadingOrderTraversalPolicy) for focus
traversal is pretty good: It gives the right answer for most applications.
However, there are always pathological cases, or cases where the context or
design requires a different order than the one the default ordering algorithm
arrives at. For those cases, there are other mechanisms for achieving the
desired order.
