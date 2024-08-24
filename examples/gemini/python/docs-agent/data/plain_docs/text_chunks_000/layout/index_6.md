To create a Cupertino app, use CupertinoApp and CupertinoPageScaffold widgets.
Unlike Material, it doesn't provide a default banner or background color.
You need to set these yourself.

To set default colors, pass in a configured CupertinoThemeData
  to your app's theme property.

To add an iOS-styled navigation bar to the top of your app, add a
  CupertinoNavigationBar widget to the navigationBar
  property of your scaffold.
  You can use the colors that CupertinoColors provides to
  configure your widgets to match iOS design.


To lay out the body of your app, set the child property of your scaffold
  with the desired widget as its value, like Center or Column.


To learn what other UI components you can add, check out the
Cupertino library.
code-excerpt "lib/cupertino.dart (my-app)"?
```dart
class MyApp extends StatelessWidget {
  const MyApp();
@override
  Widget build(BuildContext context) {
    return const CupertinoApp(
      title: 'Flutter layout demo',
      theme: CupertinoThemeData(
        brightness: Brightness.light,
        primaryColor: CupertinoColors.systemBlue,
      ),
      home: CupertinoPageScaffold(
        navigationBar: CupertinoNavigationBar(
          backgroundColor: CupertinoColors.systemGrey,
          middle: Text('Flutter layout demo'),
        ),
        child: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Text('Hello World'),
            ],
          ),
        ),
      ),
    );
  }
}
```
:::note
The Cupertino library implements widgets that follow
Apple's Human Interface Guidelines for iOS.
When designing your UI, you can use
widgets from the standard widgets library, or the Cupertino library.
You can mix widgets from both libraries, you can customize existing widgets,
or you can build your own set of custom widgets.
:::
