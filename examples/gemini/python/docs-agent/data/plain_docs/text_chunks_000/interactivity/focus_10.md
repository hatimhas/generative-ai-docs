The Focus.onFocusChanged callback can be used to get notifications that the
focus state for a particular node has changed. It notifies if the node is added
to or removed from the focus chain, which means it gets notifications even if it
isn't the primary focus. If you only want to know if you have received the
primary focus, check and see if hasPrimaryFocus is true on the focus node.
