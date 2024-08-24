One of the core interactions for both touch-based and
pointer-based inputs is drag and drop. Although this
interaction is expected for both types of input,
there are important differences to think about when
it comes to scrolling lists of draggable items.
Generally speaking, touch users expect to see drag handles
to differentiate draggable areas from scrollable ones,
or alternatively, to initiate a drag by using a long
press gesture. This is because scrolling and dragging
are both sharing a single finger for input.
Mouse users have more input options. They can use a wheel
or scrollbar to scroll, which generally eliminates the need
for dedicated drag handles. If you look at the macOS
Finder or Windows Explorer, you'll see that they work
this way: you just select an item and start dragging.
In Flutter, you can implement drag and drop in many ways.
Discussing specific implementations is outside
the scope of this article, but some high level options
include the following:


Use the Draggable and DragTarget APIs
  directly for a custom look and feel.


Hook into onPan gesture events,
  and move an object yourself within a parent Stack.


Use one of the pre-made list packages on pub.dev.
