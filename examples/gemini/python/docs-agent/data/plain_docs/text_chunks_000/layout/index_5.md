For a Material app, you can use a Scaffold widget;
it provides a default banner, background color,
and has API for adding drawers, snack bars, and bottom sheets.
Then you can add the Center widget directly to the body
property for the home page.
code-excerpt path-base="layout/base"?
code-excerpt "lib/main.dart (my-app)"?
```dart
class MyApp extends StatelessWidget {
  const MyApp();
@override
  Widget build(BuildContext context) {
    const String appTitle = 'Flutter layout demo';
    return MaterialApp(
      title: appTitle,
      home: Scaffold(
        appBar: AppBar(
          title: const Text(appTitle),
        ),
        body: const Center(
          child: Text('Hello World'),
        ),
      ),
    );
  }
}
```
:::note
The Material library implements widgets that follow [Material
Design][] principles. When designing your UI, you can exclusively use
widgets from the standard widgets library, or you can use
widgets from the Material library. You can mix widgets from both
libraries, you can customize existing widgets,
or you can build your own set of custom widgets.
:::
