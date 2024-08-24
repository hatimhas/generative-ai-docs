code-excerpt "lib/main.dart (Example26)" replace="/(return |;)//g"?
dart
Row(
  children: [
    Expanded(
      child: Container(
        color: red,
        child: const Text(
          'This is a very long text that won\'t fit the line.',
          style: big,
        ),
      ),
    ),
    Expanded(
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
If all of Row's children are wrapped in Expanded widgets,
each Expanded has a size proportional to its flex parameter,
and only then each Expanded widget forces its child to have
the Expanded's width.
In other words, Expanded ignores the preferred width of
its children.
