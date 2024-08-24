In this section, shell out the basic Flutter app code to start your app.
code-excerpt path-base="layout/base"?


Set up your Flutter environment.


Create a new Flutter app.


Replace the contents of lib/main.dart with the following code.
   This app uses a parameter for the app title and the title shown
   on the app's appBar. This decision simplifies the code.


code-excerpt "lib/main.dart (all)"?
```dart
   import 'package:flutter/material.dart';
void main() => runApp(const MyApp());
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
