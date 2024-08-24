code-excerpt "lib/main.dart (Example22)" replace="/(return |;)//g"?
dart
FittedBox(
  child: Container(
    height: 20,
    width: double.infinity,
    color: Colors.red,
  ),
)
FittedBox can only scale a widget that is bounded
(has non-infinite width and height). Otherwise,
it won't render anything,
and you'll see an error in the console.
