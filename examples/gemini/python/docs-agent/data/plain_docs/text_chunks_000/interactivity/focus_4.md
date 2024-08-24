Some dos and don'ts around using these objects include:

Don't allocate a new FocusNode for each build.  This can cause
  memory leaks, and occasionally causes a loss of focus when the widget
  rebuilds while the node has focus.
Do create FocusNode and FocusScopeNode objects in a stateful widget.
  FocusNode and FocusScopeNode need to be disposed of when you're done
  using them, so they should only be created inside of a stateful widget's
  state object, where you can override dispose to dispose of them.
Don't use the same FocusNode for multiple widgets. If you do, the
  widgets will fight over managing the attributes of the node, and you
  probably won't get what you expect.
Do set the debugLabel of a focus node widget to help with diagnosing
  focus issues.
Don't set the onKeyEvent callback on a FocusNode or FocusScopeNode if
  they are being managed by a Focus or FocusScope widget.
  If you want an onKeyEvent handler, then add a new Focus widget
  around the widget subtree you would like to listen to, and
  set the onKeyEvent attribute of the widget to your handler.
  Set canRequestFocus: false on the widget if
  you also don't want it to be able to take primary focus.
  This is because the onKeyEvent attribute on the Focus widget can be
  set to something else in a subsequent build, and if that happens,
  it overwrites the onKeyEvent handler you set on the node.
Do call requestFocus() on a node to request that it receives the
  primary focus, especially from an ancestor that has passed a node it owns to
  a descendant where you want to focus.
Do use focusNode.requestFocus(). It is not necessary to call
  FocusScope.of(context).requestFocus(focusNode). The
  focusNode.requestFocus() method is equivalent and more performant.
