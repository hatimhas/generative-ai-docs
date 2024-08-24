Most applications include some form of user interaction with the system.
The first step in building an interactive application is to detect
input gestures. See how that works by creating a simple button:
code-excerpt "lib/main_mybutton.dart"?
```dartpad title="Flutter button hands-on example in DartPad" run="true"
import 'package:flutter/material.dart';
class MyButton extends StatelessWidget {
  const MyButton();
@override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: () {
        print('MyButton was tapped!');
      },
      child: Container(
        height: 50,
        padding: const EdgeInsets.all(8),
        margin: const EdgeInsets.symmetric(horizontal: 8),
        decoration: BoxDecoration(
          borderRadius: BorderRadius.circular(5),
          color: Colors.lightGreen[500],
        ),
        child: const Center(
          child: Text('Engage'),
        ),
      ),
    );
  }
}
void main() {
  runApp(
    const MaterialApp(
      home: Scaffold(
        body: Center(
          child: MyButton(),
        ),
      ),
    ),
  );
}
```
The GestureDetector widget doesn't have a visual
representation but instead detects gestures made by the
user. When the user taps the Container,
the GestureDetector calls its onTap() callback, in this
case printing a message to the console. You can use
GestureDetector to detect a variety of input gestures,
including taps, drags, and scales.
Many widgets use a GestureDetector to provide
optional callbacks for other widgets. For example, the
IconButton, ElevatedButton, and
FloatingActionButton widgets have onPressed()
callbacks that are triggered when the user taps the widget.
For more information, check out Gestures in Flutter.
