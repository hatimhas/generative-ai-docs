code-excerpt path-base="ui/widgets_intro/"?

Flutter widgets are built using a modern framework that takes
inspiration from React. The central idea is that you build
your UI out of widgets. Widgets describe what their view
should look like given their current configuration and state.
When a widget's state changes, the widget rebuilds its description,
which the framework diffs against the previous description in order
to determine the minimal changes needed in the underlying render
tree to transition from one state to the next.
:::note
If you would like to become better acquainted with Flutter by diving
into some code, check out building layouts,
and adding interactivity to your Flutter app.
:::
The minimal Flutter app simply calls the runApp()
function with a widget:
code-excerpt "lib/main.dart"?
```dartpad title="Flutter Hello World hands-on example in DartPad" run="true"
import 'package:flutter/material.dart';
void main() {
  runApp(
    const Center(
      child: Text(
        'Hello, world!',
        textDirection: TextDirection.ltr,
      ),
    ),
  );
}
```
The runApp() function takes the given
Widget and makes it the root of the widget tree.
In this example, the widget tree consists of two widgets,
the Center widget and its child, the Text widget.
The framework forces the root widget to cover the screen,
which means the text "Hello, world" ends up centered on screen.
The text direction needs to be specified in this instance;
when the MaterialApp widget is used,
this is taken care of for you, as demonstrated later.
When writing an app, you'll commonly author new widgets that
are subclasses of either StatelessWidget or StatefulWidget,
depending on whether your widget manages any state.
A widget's main job is to implement a build() function,
which describes the widget in terms of other, lower-level widgets.
The framework builds those widgets in turn until the process
bottoms out in widgets that represent the underlying RenderObject,
which computes and describes the geometry of the widget.
