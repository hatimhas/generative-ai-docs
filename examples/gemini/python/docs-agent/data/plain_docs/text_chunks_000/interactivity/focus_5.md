There is an API for telling a node to "give up the focus", named
FocusNode.unfocus(). While it does remove focus from the node, it is important
to realize that there really is no such thing as "unfocusing" all nodes. If a
node is unfocused, then it must pass the focus somewhere else, since there is
always a primary focus. The node that receives the focus when a node calls
unfocus() is either the nearest FocusScopeNode, or a previously focused node
in that scope, depending upon the disposition argument given to unfocus().
If you would like more control over where the focus goes when you remove it from
a node, explicitly focus another node instead of calling unfocus(), or use the
focus traversal mechanism to find another node with the focusInDirection,
nextFocus, or previousFocus methods on FocusNode.
When calling unfocus(), the disposition argument allows two modes for
unfocusing: UnfocusDisposition.scope and
UnfocusDisposition.previouslyFocusedChild. The default is scope, which gives
the focus to the nearest parent focus scope. This means that if the focus is
thereafter moved to the next node with FocusNode.nextFocus, it starts with the
"first" focusable item in the scope.
The previouslyFocusedChild disposition will search the scope to find the
previously focused child and request focus on it. If there is no previously
focused child, it is equivalent to scope.
:::secondary Beware
If there is no other scope, then focus moves to the root scope node of
the focus system, FocusManager.rootScope. This is generally not desirable, as
the root scope doesn't have a context for the framework to determine which
node should be focused next. If you find that your application suddenly loses
the ability to navigate by using focus traversal, this is probably what has
happened.  To fix it, add a FocusScope as an ancestor to the focus node that
is requesting the unfocus. The WidgetsApp (from which MaterialApp and
CupertinoApp are derived) has its own FocusScope, so this should not be an
issue if you are using those.
:::
