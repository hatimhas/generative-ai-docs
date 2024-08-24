Add your custom stateful widget to the widget tree in
the app's build() method. First, locate the code that
creates the Icon and Text, and delete it.
In the same location, create the stateful widget:
code-excerpt path-base=""?
dart diff
  child: Row(
    children: [
      // ...
-     Icon(
-       Icons.star,
-       color: Colors.red[500],
-     ),
-     const Text('41'),
+     const FavoriteWidget(),
    ],
  ),
That's it! When you hot reload the app,
the star icon should now respond to taps.
