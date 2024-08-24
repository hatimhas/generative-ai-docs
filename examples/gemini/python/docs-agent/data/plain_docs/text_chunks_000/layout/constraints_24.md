code-excerpt "lib/main.dart (Example16)" replace="/(return |;)//g"?
dart
UnconstrainedBox(
  child: Container(color: Colors.red, width: double.infinity, height: 100),
)
This won't render anything, and you'll see an error in the console.
The UnconstrainedBox lets its child be any size it wants,
however its child is a Container with infinite size.
Flutter can't render infinite sizes, so it throws an error with
the following message: BoxConstraints forces an infinite width.
