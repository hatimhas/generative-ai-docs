code-excerpt "lib/main.dart (Example8)" replace="/(return |;)//g"?
dart
Center(
  child: Container(
    padding: const EdgeInsets.all(20),
    color: red,
    child: Container(color: green, width: 30, height: 30),
  ),
)
The red Container sizes itself to its children's size,
but it takes its own padding into consideration.
So it is also 30 × 30 plus padding.
The red color is visible because of the padding,
and the green Container has the same size as
in the previous example.
