To get more control over the order that
widgets are focused on when the user tabs through,
you can use FocusTraversalGroup to define sections
of the tree that should be treated as a group when tabbing.
For example, you might to tab through all the fields in
a form before tabbing to the submit button:
code-excerpt "lib/pages/focus_examples_page.dart (focus-traversal-group)"?
dart
return Column(children: [
  FocusTraversalGroup(
    child: MyFormWithMultipleColumnsAndRows(),
  ),
  SubmitButton(),
]);
Flutter has several built-in ways to traverse widgets and groups,
defaulting to the ReadingOrderTraversalPolicy class.
This class usually works well, but it's possible to modify this
using another predefined TraversalPolicy class or by creating
a custom policy.
