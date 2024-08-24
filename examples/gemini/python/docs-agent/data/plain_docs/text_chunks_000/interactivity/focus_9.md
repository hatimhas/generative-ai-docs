Setting the autofocus attribute of a Focus widget tells the widget to
request the focus the first time the focus scope it belongs to is focused.  If
more than one widget has autofocus set, then it is arbitrary which one
receives the focus, so try to only set it on one widget per focus scope.
The autofocus attribute only takes effect if there isn't already a focus in
the scope that the node belongs to.
Setting the autofocus attribute on two nodes that belong to different focus
scopes is well defined: each one becomes the focused widget when their
corresponding scopes are focused.
