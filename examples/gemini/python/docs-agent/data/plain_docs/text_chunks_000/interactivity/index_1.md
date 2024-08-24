:::secondary What's the point?

A stateful widget is implemented by two classes:
  a subclass of StatefulWidget and a subclass of State.
The state class contains the widget's mutable state and
  the widget's build() method.
When the widget's state changes, the state object calls
  setState(), telling the framework to redraw the widget.

:::
In this section, you'll create a custom stateful widget.
You'll replace two stateless widgets—the solid red
star and the numeric count next to it—with a single
custom stateful widget that manages a row with two
children widgets: an IconButton and Text.
Implementing a custom stateful widget requires creating two classes:

A subclass of StatefulWidget that defines the widget.
A subclass of State that contains the state for that
  widget and defines the widget's build() method.

This section shows you how to build a stateful widget,
called FavoriteWidget, for the lakes app.
After setting up, your first step is choosing how state is
managed for FavoriteWidget.
