Below are terms, as Flutter uses them, for elements of the focus system. The
various classes that implement some of these concepts are introduced below.

Focus tree - A tree of focus nodes that typically sparsely mirrors the
  widget tree, representing all the widgets that can receive focus.
Focus node - A single node in a focus tree. This node can receive the
  focus, and is said to "have focus" when it is part of the focus chain. It
  participates in handling key events only when it has focus.
Primary focus - The farthest focus node from the root of the focus tree
  that has focus. This is the focus node where key events start propagating to
  the primary focus node and its ancestors.
Focus chain - An ordered list of focus nodes that starts at the primary
  focus node and follows the branches of the focus tree to the root of the
  focus tree.
Focus scope - A special focus node whose job is to contain a group of
  other focus nodes, and allow only those nodes to receive focus. It contains
  information about which nodes were previously focused in its subtree.
Focus traversal - The process of moving from one focusable node to
  another in a predictable order. This is typically seen in applications when
  the user presses Tab to move to the next focusable control or
  field.
