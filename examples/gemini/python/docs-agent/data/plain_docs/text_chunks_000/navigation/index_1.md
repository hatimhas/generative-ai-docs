:::note
We don't recommend using named routes for most applications.
For more information, see the Limitations section below.
:::
Applications with simple navigation and deep linking requirements can use the
Navigator for navigation and the MaterialApp.routes parameter for deep
links:
dart
@override
Widget build(BuildContext context) {
  return MaterialApp(
    routes: {
      '/': (context) => HomeScreen(),
      '/details': (context) => DetailScreen(),
    },
  );
}
Routes specified here are called named routes. For a complete example, follow
the Navigate with named routes recipe from the Flutter Cookbook.
