code-excerpt "lib/main.dart (Example25)" replace="/(return |;)//g"?
dart
Row(
  children: [
    Expanded(
      child: Center(
        child: Container(
          color: red,
          child: const Text(
            'This is a very long text that won\'t fit the line.',
            style: big,
          ),
        ),
      ),
    ),
    Container(color: green, child: const Text('Goodbye!', style: big)),
  ],
)
When a Row's child is wrapped in an Expanded widget,
the Row won't let this child define its own width anymore.
Instead, it defines the Expanded width according to the
other children, and only then the Expanded widget forces
the original child to have the Expanded's width.
In other words, once you use Expanded,
the original child's width becomes irrelevant, and is ignored.
