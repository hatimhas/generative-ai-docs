responsible for different concerns; for example, one
widget might present a complex user interface
with the goal of gathering specific information,
such as a date or location, while another widget might
use that information to change the overall presentation.
In Flutter, change notifications flow "up" the widget
hierarchy by way of callbacks, while current state flows
"down" to the stateless widgets that do presentation.
The common parent that redirects this flow is the State.
The following slightly more complex example shows how
this works in practice:
code-excerpt "lib/main_counterdisplay.dart"?
dartpad title="Flutter Hello World hands-on example in DartPad" run="true"
import 'package:flutter/material.dart';
class CounterDisplay extends StatelessWidget {
  const CounterDisplay();
final int count;
@override
  Widget build(BuildContext context) {
    return Text('Count: $count');
  }
}
class CounterIncrementor extends StatelessWidget {
  const CounterIncrementor();
final VoidCallback onPressed;
@override
  Widget build(BuildContext context) {
    return ElevatedButton(
      onPressed: onPressed,
      child: const Text('Increment'),
    );
  }
}
class Counter extends StatefulWidget {
  const Counter();
@override
  State createState() => _CounterState();
}
class _CounterState extends State {
  int _counter = 0;
void _increment() {
    setState(() {
      ++_counter;
    });
  }
@override
  Widget build(BuildContext context) {
    return Row(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        CounterIncrementor(onPressed: _increment),
        const SizedBox(width: 16),
        CounterDisplay(count: _counter),
      ],
    );
  }
}
void main() {
  runApp(
    const MaterialApp(
      home: Scaffold(
        body: Center(
          child: Counter(),
        ),
      ),
    ),
  );
}
Notice the creation of two new stateless widgets,
cleanly separating the concerns of displaying the counter
(CounterDisplay) and changing the counter (CounterIncrementor).
Although the net result is the same as the previous example,
the separation of responsibility allows greater complexity to
be encapsulated in the individual widgets,
while maintaining simplicity in the parent.
For more information, check out:
StatefulWidget
setState()
