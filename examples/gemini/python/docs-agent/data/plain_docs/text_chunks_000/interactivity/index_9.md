Sometimes it makes the most sense for the widget
to manage its state internally. For example,
ListView automatically scrolls when its
content exceeds the render box. Most developers
using ListView don't want to manage ListView's
scrolling behavior, so ListView itself manages its scroll offset.
The _TapboxAState class:

Manages state for TapboxA.
Defines the _active boolean which determines the
  box's current color.
Defines the _handleTap() function, which updates
  _active when the box is tapped and calls the
  setState() function to update the UI.
Implements all interactive behavior for the widget.

code-excerpt path-base="ui/interactive/"?
code-excerpt "lib/self_managed.dart"?
```dart
import 'package:flutter/material.dart';
// TapboxA manages its own state.
//------------------------- TapboxA ----------------------------------
class TapboxA extends StatefulWidget {
  const TapboxA();
@override
  State createState() => _TapboxAState();
}
class _TapboxAState extends State {
  bool _active = false;
void _handleTap() {
    setState(() {
      _active = !_active;
    });
  }
@override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: _handleTap,
      child: Container(
        width: 200,
        height: 200,
        decoration: BoxDecoration(
          color: _active ? Colors.lightGreen[700] : Colors.grey[600],
        ),
        child: Center(
          child: Text(
            _active ? 'Active' : 'Inactive',
            style: const TextStyle(fontSize: 32, color: Colors.white),
          ),
        ),
      ),
    );
  }
}
//------------------------- MyApp ----------------------------------
class MyApp extends StatelessWidget {
  const MyApp();
@override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      home: Scaffold(
        appBar: AppBar(
          title: const Text('Flutter Demo'),
        ),
        body: const Center(
          child: TapboxA(),
        ),
      ),
    );
  }
}
```
