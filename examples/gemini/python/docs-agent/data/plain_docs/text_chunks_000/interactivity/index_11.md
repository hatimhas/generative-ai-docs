For some widgets, a mix-and-match approach makes
the most sense. In this scenario, the stateful widget
manages some of the state, and the parent widget
manages other aspects of the state.
In the TapboxC example, on tap down,
a dark green border appears around the box. On tap up,
the border disappears and the box's color changes. TapboxC
exports its _active state to its parent but manages its
_highlight state internally. This example has two State
objects, _ParentWidgetState and _TapboxCState.
The _ParentWidgetState object:

Manages the _active state.
Implements _handleTapboxChanged(),
  the method called when the box is tapped.
Calls setState() to update the UI when a tap
  occurs and the _active state changes.

The _TapboxCState object:

Manages the _highlight state.
The GestureDetector listens to all tap events.
  As the user taps down, it adds the highlight
  (implemented as a dark green border). As the user releases the
  tap, it removes the highlight.
Calls setState() to update the UI on tap down,
  tap up, or tap cancel, and the _highlight state changes.
On a tap event, passes that state change to the parent widget to take
  appropriate action using the widget property.

code-excerpt "lib/mixed.dart"?
```dart
import 'package:flutter/material.dart';
//---------------------------- ParentWidget ----------------------------
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
      child: TapboxC(
        active: _active,
        onChanged: _handleTapboxChanged,
      ),
    );
  }
}
//----------------------------- TapboxC ------------------------------
class TapboxC extends StatefulWidget {
  const TapboxC({
    super.key,
    this.active = false,
    required this.onChanged,
  });
final bool active;
  final ValueChanged onChanged;
@override
  State createState() => _TapboxCState();
}
class _TapboxCState extends State {
  bool _highlight = false;
void _handleTapDown(TapDownDetails details) {
    setState(() {
      _highlight = true;
    });
  }
void _handleTapUp(TapUpDetails details) {
    setState(() {
      _highlight = false;
    });
  }
void _handleTapCancel() {
    setState(() {
      _highlight = false;
    });
  }
void _handleTap() {
    widget.onChanged(!widget.active);
  }
@override
  Widget build(BuildContext context) {
    // This example adds a green border on tap down.
    // On tap up, the square changes to the opposite state.
    return GestureDetector(
      onTapDown: _handleTapDown, // Handle the tap events in the order that
      onTapUp: _handleTapUp, // they occur: down, up, tap, cancel
      onTap: _handleTap,
      onTapCancel: _handleTapCancel,
      child: Container(
        width: 200,
        height: 200,
        decoration: BoxDecoration(
          color: widget.active ? Colors.lightGreen[700] : Colors.grey[600],
          border: _highlight
              ? Border.all(
                  color: Colors.teal[700]!,
                  width: 10,
                )
              : null,
        ),
        child: Center(
          child: Text(widget.active ? 'Active' : 'Inactive',
              style: const TextStyle(fontSize: 32, color: Colors.white)),
        ),
      ),
    );
  }
}
```
An alternate implementation might have exported the highlight
state to the parent while keeping the active state internal,
but if you asked someone to use that tap box,
they'd probably complain that it doesn't make much sense.
The developer cares whether the box is active.
The developer probably doesn't care how the highlighting
is managed, and prefers that the tap box handles those
details.
