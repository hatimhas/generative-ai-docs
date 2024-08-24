The FocusNode and FocusScopeNode objects implement the
mechanics of the focus system. They are long-lived objects (longer than widgets,
similar to render objects) that hold the focus state and attributes so that they
are persistent between builds of the widget tree. Together, they form
the focus tree data structure.
They were originally intended to be developer-facing objects used to control
some aspects of the focus system, but over time they have evolved to mostly
implement details of the focus system. In order to prevent breaking existing
applications, they still contain public interfaces for their attributes. But, in
general, the thing for which they are most useful is to act as a relatively
opaque handle, passed to a descendant widget in order to call requestFocus()
on an ancestor widget, which requests that a descendant widget obtain focus.
Setting of the other attributes is best managed by a Focus or
FocusScope widget, unless you are not using them, or implementing your own
version of them.
