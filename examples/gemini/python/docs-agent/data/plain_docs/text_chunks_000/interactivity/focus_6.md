The Focus widget owns and manages a focus node, and is the workhorse of the
focus system.  It manages the attaching and detaching of the focus node it owns
from the focus tree, manages the attributes and callbacks of the focus node, and
has static functions to enable discovery of focus nodes attached to the widget
tree.
In its simplest form, wrapping the Focus widget around a widget subtree allows
that widget subtree to obtain focus as part of the focus traversal process, or
whenever requestFocus is called on the FocusNode passed to it. When combined
with a gesture detector that calls requestFocus, it can receive focus when
tapped or clicked.
You might pass a FocusNode object to the Focus widget to manage, but if you
don't, it creates its own. The main reason to create your own
FocusNode is to be able to call requestFocus()
on the node to control the focus from a parent widget. Most of the other
functionality of a FocusNode is best accessed by changing the attributes of
the Focus widget itself.
The Focus widget is used in most of Flutter's own controls to implement their
focus functionality.
Here is an example showing how to use the Focus widget to make a custom
control focusable. It creates a container with text that reacts to receiving the
focus.
code-excerpt "ui/advanced/focus/lib/custom_control_example.dart"?
```dart
import 'package:flutter/material.dart';
void main() => runApp(const MyApp());
class MyApp extends StatelessWidget {
  const MyApp();
  static const String _title = 'Focus Sample';
@override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: _title,
      home: Scaffold(
        appBar: AppBar(title: const Text(_title)),
        body: const Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [MyCustomWidget(), MyCustomWidget()],
        ),
      ),
    );
  }
}
class MyCustomWidget extends StatefulWidget {
  const MyCustomWidget();
@override
  State createState() => _MyCustomWidgetState();
}
class _MyCustomWidgetState extends State {
  Color _color = Colors.white;
  String _label = 'Unfocused';
@override
  Widget build(BuildContext context) {
    return Focus(
      onFocusChange: (focused) {
        setState(() {
          _color = focused ? Colors.black26 : Colors.white;
          _label = focused ? 'Focused' : 'Unfocused';
        });
      },
      child: Center(
        child: Container(
          width: 300,
          height: 50,
          alignment: Alignment.center,
          color: _color,
          child: Text(_label),
        ),
      ),
    );
  }
}
```
