Flutter comes with a suite of powerful basic widgets,
of which the following are commonly used:
Text
: The Text widget lets you create a run of styled text
  within your application.
Row, Column
: These flex widgets let you create flexible layouts in
  both the horizontal (Row) and vertical (Column) directions.
  The design of these objects is based on the web's
  flexbox layout model.
Stack
: Instead of being linearly oriented (either horizontally or vertically),
  a Stack widget lets you place widgets on top of each other in paint order.
  You can then use the Positioned widget on children of a
  Stack to position them relative to the top, right, bottom,
  or left edge of the stack. Stacks are based on the web's
  absolute positioning layout model.
Container
: The Container widget lets you create a rectangular visual element.
  A container can be decorated with a BoxDecoration, such as a
  background, a border, or a shadow. A Container can also have margins,
  padding, and constraints applied to its size. In addition, a
  Container can be transformed in three-dimensional space using a matrix.
Below are some simple widgets that combine these and other widgets:
code-excerpt "lib/main_myappbar.dart"?
```dartpad title="Flutter combining widgets hands-on example in DartPad" run="true"
import 'package:flutter/material.dart';
class MyAppBar extends StatelessWidget {
  const MyAppBar();
// Fields in a Widget subclass are always marked "final".
final Widget title;
@override
  Widget build(BuildContext context) {
    return Container(
      height: 56, // in logical pixels
      padding: const EdgeInsets.symmetric(horizontal: 8),
      decoration: BoxDecoration(color: Colors.blue[500]),
      // Row is a horizontal, linear layout.
      child: Row(
        children: [
          const IconButton(
            icon: Icon(Icons.menu),
            tooltip: 'Navigation menu',
            onPressed: null, // null disables the button
          ),
          // Expanded expands its child
          // to fill the available space.
          Expanded(
            child: title,
          ),
          const IconButton(
            icon: Icon(Icons.search),
            tooltip: 'Search',
            onPressed: null,
          ),
        ],
      ),
    );
  }
}
class MyScaffold extends StatelessWidget {
  const MyScaffold();
@override
  Widget build(BuildContext context) {
    // Material is a conceptual piece
    // of paper on which the UI appears.
    return Material(
      // Column is a vertical, linear layout.
      child: Column(
        children: [
          MyAppBar(
            title: Text(
              'Example title',
              style: Theme.of(context) //
                  .primaryTextTheme
                  .titleLarge,
            ),
          ),
          const Expanded(
            child: Center(
              child: Text('Hello, world!'),
            ),
          ),
        ],
      ),
    );
  }
}
void main() {
  runApp(
    const MaterialApp(
      title: 'My app', // used by the OS task switcher
      home: SafeArea(
        child: MyScaffold(),
      ),
    ),
  );
}
```
Be sure to have a uses-material-design: true entry in the flutter
section of your pubspec.yaml file. It allows you to use the predefined
set of Material icons. It's generally a good idea to include this line
if you are using the Materials library.
yaml
name: my_app
flutter:
  uses-material-design: true
Many Material Design widgets need to be inside of a MaterialApp
to display properly, in order to inherit theme data.
Therefore, run the application with a MaterialApp.
The MyAppBar widget creates a Container with a height of 56
device-independent pixels with an internal padding of 8 pixels,
both on the left and the right. Inside the container,
MyAppBar uses a Row layout to organize its children.
The middle child, the title widget, is marked as Expanded,
which means it expands to fill any remaining available space
that hasn't been consumed by the other children.
You can have multiple Expanded children and determine the
ratio in which they consume the available space using the
flex argument to Expanded.
The MyScaffold widget organizes its children in a vertical column.
At the top of the column it places an instance of MyAppBar,
passing the app bar a Text widget to use as its title.
Passing widgets as arguments to other widgets is a powerful technique
that lets you create generic widgets that can be reused in a wide
variety of ways. Finally, MyScaffold uses an
Expanded to fill the remaining space with its body,
which consists of a centered message.
For more information, check out Layouts.
