One of the details of the focus system is that when focus is requested, it only
takes effect after the current build phase completes.  This means that focus
changes are always delayed by one frame, because changing focus can
cause arbitrary parts of the widget tree to rebuild, including ancestors of the
widget currently requesting focus. Because descendants cannot dirty their
ancestors, it has to happen between frames, so that any needed changes can
happen on the next frame.
