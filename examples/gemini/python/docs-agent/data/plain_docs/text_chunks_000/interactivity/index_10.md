Often it makes the most sense for the parent widget
to manage the state and tell its child widget when to update.
For example, IconButton allows you to treat
an icon as a tappable button. IconButton is a
stateless widget because we decided that the parent
widget needs to know whether the button has been tapped,
so it can take appropriate action.
In the following example, TapboxB exports its state
to its parent through a callback. Because TapboxB
doesn't manage any state, it subclasses StatelessWidget.
The ParentWidgetState class:

Manages the _active state for TapboxB.
Implements _handleTapboxChanged(),
  the method called when the box is tapped.
When the state changes, calls setState()
  to update the UI.

The TapboxB class:

Extends StatelessWidget because all state is handled by its parent.
When a tap is detected, it notifies the parent.

code-excerpt "lib/parent_managed.dart"?
```dart
import 'package:flutter/material.dart';
// ParentWidget manages the state for TapboxB.
//------------------------ ParentWidget --------------------------------
class ParentWidget extends StatefulWidget {
  const ParentWidget();
@override
  State createState() => _ParentWidgetState();
}
class _ParentWidgetState extends State {
  bool _active = false;
void _handleTapboxChanged(bool newValue) {
    setState(() {
      _active = newValue;
    });
  }
@override
  Widget build(BuildContext context) {
    return SizedBox(
      child: TapboxB(
        active: _active,
        onChanged: _handleTapboxChanged,
      ),
    );
  }
}
//------------------------- TapboxB ----------------------------------
class TapboxB extends StatelessWidget {
  const TapboxB({
    super.key,
    this.active = false,
    required this.onChanged,
  });
final bool active;
  final ValueChanged onChanged;
void _handleTap() {
    onChanged(!active);
  }
@override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: _handleTap,
      child: Container(
        width: 200,
        height: 200,
        decoration: BoxDecoration(
          color: active ? Colors.lightGreen[700] : Colors.grey[600],
        ),
        child: Center(
          child: Text(
            active ? 'Active' : 'Inactive',
            style: const TextStyle(fontSize: 32, color: Colors.white),
          ),
        ),
      ),
    );
  }
}
```
