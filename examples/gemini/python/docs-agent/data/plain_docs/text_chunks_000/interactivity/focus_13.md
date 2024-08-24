The FocusScope widget is a special version of the Focus widget that manages
a FocusScopeNode instead of a FocusNode.  The FocusScopeNode is a special
node in the focus tree that serves as a grouping mechanism for the focus nodes
in a subtree. Focus traversal stays within a focus scope unless a node outside
of the scope is explicitly focused.
The focus scope also keeps track of the current focus and history of the nodes
focused within its subtree.  That way, if a node releases focus or is removed
when it had focus, the focus can be returned to the node that had focus
previously.
Focus scopes also serve as a place to return focus to if none of the descendants
have focus.  This allows the focus traversal code to have a starting context for
finding the next (or first) focusable control to move to.
If you focus a focus scope node, it first attempts to focus the current, or most
recently focused node in its subtree, or the node in its subtree that requested
autofocus (if any).  If there is no such node, it receives the focus itself.
