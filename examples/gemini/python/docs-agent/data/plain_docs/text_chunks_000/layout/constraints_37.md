code-excerpt "lib/main.dart (Example29)" replace="/(return |;)//g"?
dart
Scaffold(
  body: SizedBox.expand(
    child: Container(
      color: blue,
      child: const Column(
        children: [
          Text('Hello!'),
          Text('Goodbye!'),
        ],
      ),
    ),
  ),
)
If you want the Scaffold's child to be exactly the same size
as the Scaffold itself, you can wrap its child with
SizedBox.expand.
