One of the main aspects of focus is controlling what can receive focus and how.
The attributes canRequestFocus, skipTraversal, and descendantsAreFocusable
control how this node and its descendants participate in the focus process.
If the skipTraversal attribute true, then this focus node doesn't participate
in focus traversal. It is still focusable if requestFocus is called on its
focus node, but is otherwise skipped when the focus traversal system is looking
for the next thing to focus on.
The canRequestFocus attribute, unsurprisingly, controls whether or not the
focus node that this Focus widget manages can be used to request focus. If
this attribute is false, then calling requestFocus on the node has no effect.
It also implies that this node is skipped for focus traversal, since it can't
request focus.
The descendantsAreFocusable attribute controls whether the descendants of this
node can receive focus, but still allows this node to receive focus.  This
attribute can be used to turn off focusability for an entire widget subtree.
This is how the ExcludeFocus widget works: it's just a Focus widget with
this attribute set.
