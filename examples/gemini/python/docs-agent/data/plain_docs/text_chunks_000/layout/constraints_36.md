code-excerpt "lib/main.dart (Example28)" replace="/(return |;)//g"?
dart
Scaffold(
  body: Container(
    color: blue,
    child: const Column(
      children: [
        Text('Hello!'),
        Text('Goodbye!'),
      ],
    ),
  ),
)
The screen forces the Scaffold to be exactly the same size
as the screen, so the Scaffold fills the screen.
The Scaffold tells the Container that it can be any size it wants,
but not bigger than the screen.
:::note
When a widget tells its child that it can be smaller than a
certain size, we say the widget supplies loose constraints
to its child. More on that later.
:::
