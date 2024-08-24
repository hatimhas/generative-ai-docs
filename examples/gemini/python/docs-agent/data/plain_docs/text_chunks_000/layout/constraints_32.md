code-excerpt "lib/main.dart (Example24)" replace="/(return |;)//g"?
dart
Row(
  children: [
    Container(
      color: red,
      child: const Text(
        'This is a very long text that '
        'won\'t fit the line.',
        style: big,
      ),
    ),
    Container(color: green, child: const Text('Goodbye!', style: big)),
  ],
)
Since Row won't impose any constraints onto its children,
it's quite possible that the children might be too big to fit
the available width of the Row. In this case, just like an
UnconstrainedBox, the Row displays the "overflow warning".
