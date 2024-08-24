The FocusManager maintains the current primary focus for the system. It
only has a few pieces of API that are useful to users of the focus system. One
is the FocusManager.instance.primaryFocus property, which contains the
currently focused focus node and is also accessible from the global
primaryFocus field.
Other useful properties are FocusManager.instance.highlightMode and
FocusManager.instance.highlightStrategy. These are used by widgets that need
to switch between a "touch" mode and a "traditional" (mouse and keyboard) mode
for their focus highlights. When a user is using touch to navigate, the focus
highlight is usually hidden, and when they switch to a mouse or keyboard, the
focus highlight needs to be shown again so they know what is focused. The
hightlightStrategy tells the focus manager how to interpret changes in the
usage mode of the device: it can either automatically switch between the two
based on the most recent input events, or it can be locked in touch or
traditional modes. The provided widgets in Flutter already know how to use this
information, so you only need it if you're writing your own controls from
scratch. You can use addHighlightModeListener callback to listen for changes
in the highlight mode.
