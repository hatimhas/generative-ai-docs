code-excerpt "lib/main.dart (Example27)" replace="/(return |;)//g"?
dart
Row(
  children: [
    Flexible(
      child: Container(
        color: red,
        child: const Text(
          'This is a very long text that won\'t fit the line.',
          style: big,
        ),
      ),
    ),
    Flexible(
      child: Container(
        color: green,
        child: const Text(
          'Goodbye!',
          style: big,
        ),
      ),
    ),
  ],
)
The only difference if you use Flexible instead of Expanded,
is that Flexible lets its child have the same or smaller
width than the Flexible itself, while Expanded forces
its child to have the exact same width of the Expanded.
But both Expanded and Flexible ignore their children's width
when sizing themselves.
:::note
This means that it's impossible to expand Row children
proportionally to their sizes. The Row either uses
the exact child's width, or ignores it completely
when you use Expanded or Flexible.
:::
