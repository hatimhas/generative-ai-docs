code-excerpt path-base="layout/base"?
All layout widgets have either of the following:

A child property if they take a single child—for example,
  Center or Container
A children property if they take a list of widgets—for example,
  Row, Column, ListView, or Stack.

Add the Text widget to the Center widget:
code-excerpt "lib/main.dart (centered-text)" replace="/body: //g"?
dart
const Center(
  child: Text('Hello World'),
),
