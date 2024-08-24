:::secondary What's the point?
* How to add basic animation to a widget using addListener() and
  setState().
* Every time the Animation generates a new number, the addListener()
  function calls setState().
* How to define an AnimationController with the required
  vsync parameter.
* Understanding the ".." syntax in "..addListener",
  also known as Dart's cascade notation.
* To make a class private, start its name with an underscore (_).
:::
So far you've learned how to generate a sequence of numbers over time.
Nothing has been rendered to the screen. To render with an
Animation object, store the Animation object as a
member of your widget, then use its value to decide how to draw.
Consider the following app that draws the Flutter logo without animation:
code-excerpt "animate0/lib/main.dart"?
```dart
import 'package:flutter/material.dart';
void main() => runApp(const LogoApp());
class LogoApp extends StatefulWidget {
  const LogoApp();
@override
  State createState() => _LogoAppState();
}
class _LogoAppState extends State {
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Container(
        margin: const EdgeInsets.symmetric(vertical: 10),
        height: 300,
        width: 300,
        child: const FlutterLogo(),
      ),
    );
  }
}
```
App source: animate0
The following shows the same code modified to animate the
logo to grow from nothing to full size.
When defining an AnimationController, you must pass in a
vsync object. The vsync parameter is described in the
AnimationController section.
The changes from the non-animated example are highlighted:
dart diff
- class _LogoAppState extends State<LogoApp> {
+ class _LogoAppState extends State<LogoApp> with SingleTickerProviderStateMixin {
+   late Animation<double> animation;
+   late AnimationController controller;
+ 
+   @override
+   void initState() {
+     super.initState();
+     controller =
+         AnimationController(duration: const Duration(seconds: 2), vsync: this);
+     animation = Tween<double>(begin: 0, end: 300).animate(controller)
+       ..addListener(() {
+         setState(() {
+           // The state that has changed here is the animation object's value.
+         });
+       });
+     controller.forward();
+   }
+ 
    @override
    Widget build(BuildContext context) {
      return Center(
        child: Container(
          margin: const EdgeInsets.symmetric(vertical: 10),
-         height: 300,
-         width: 300,
+         height: animation.value,
+         width: animation.value,
          child: const FlutterLogo(),
        ),
      );
    }
+ 
+   @override
+   void dispose() {
+     controller.dispose();
+     super.dispose();
+   }
  }
App source: animate1
The addListener() function calls setState(),
so every time the Animation generates a new number,
the current frame is marked dirty, which forces
build() to be called again. In build(),
the container changes size because its height and
width now use animation.value instead of a hardcoded value.
Dispose of the controller when the State object is
discarded to prevent memory leaks.
With these few changes,
you've created your first animation in Flutter!
:::tip Dart language trick
You might not be familiar with Dart's cascade notation—the two
dots in ..addListener(). This syntax means that the addListener()
method is called with the return value from animate().
Consider the following example:
code-excerpt "animate1/lib/main.dart (add-listener)"?
dart highlightLines=2
animation = Tween<double>(begin: 0, end: 300).animate(controller)
  ..addListener(() {
    // ···
  });
This code is equivalent to:
code-excerpt "animate1/lib/main.dart (add-listener)" replace="/animation.*/$&;/g; /  \./animation/g;"?
dart highlightLines=2
animation = Tween<double>(begin: 0, end: 300).animate(controller);
animation.addListener(() {
    // ···
  });
To learn more about cascades,
check out Cascade notation
in the Dart language documentation.
:::
