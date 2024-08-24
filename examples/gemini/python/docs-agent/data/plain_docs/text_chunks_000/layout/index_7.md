For a non-Material app, you can add the Center widget to the app's
build() method:
code-excerpt path-base="layout/non_material"?
code-excerpt "lib/main.dart (my-app)"?
```dart
class MyApp extends StatelessWidget {
  const MyApp();
@override
  Widget build(BuildContext context) {
    return Container(
      decoration: const BoxDecoration(color: Colors.white),
      child: const Center(
        child: Text(
          'Hello World',
          textDirection: TextDirection.ltr,
          style: TextStyle(
            fontSize: 32,
            color: Colors.black87,
          ),
        ),
      ),
    );
  }
}
```
By default, a non-Material app doesn't include an AppBar, title,
or background color. If you want these features in a non-Material app,
you have to build them yourself. This app changes the background
color to white and the text to dark grey to mimic a Material app.



  That's it! When you run the app, you should see _Hello World_.

  App source code:

  * [Material app](}/layout/base)
  * [Non-Material app](}/layout/non_material)
