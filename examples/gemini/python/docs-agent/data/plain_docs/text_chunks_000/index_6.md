What follows is a more complete example that brings together
these concepts: A hypothetical shopping application displays various
products offered for sale, and maintains a shopping cart for
intended purchases. Start by defining the presentation class,
ShoppingListItem:
code-excerpt "lib/main_shoppingitem.dart"?
```dartpad title="Flutter complete shopping list item hands-on example in DartPad" run="true"
import 'package:flutter/material.dart';
class Product {
  const Product();
final String name;
}
typedef CartChangedCallback = Function(Product product, bool inCart);
class ShoppingListItem extends StatelessWidget {
  ShoppingListItem({
    required this.product,
    required this.inCart,
    required this.onCartChanged,
  }) : super(key: ObjectKey(product));
final Product product;
  final bool inCart;
  final CartChangedCallback onCartChanged;
Color _getColor(BuildContext context) {
    // The theme depends on the BuildContext because different
    // parts of the tree can have different themes.
    // The BuildContext indicates where the build is
    // taking place and therefore which theme to use.
return inCart //
    ? Colors.black54
    : Theme.of(context).primaryColor;
}
TextStyle? _getTextStyle(BuildContext context) {
    if (!inCart) return null;
return const TextStyle(
  color: Colors.black54,
  decoration: TextDecoration.lineThrough,
);
}
@override
  Widget build(BuildContext context) {
    return ListTile(
      onTap: () {
        onCartChanged(product, inCart);
      },
      leading: CircleAvatar(
        backgroundColor: _getColor(context),
        child: Text(product.name[0]),
      ),
      title: Text(product.name, style: _getTextStyle(context)),
    );
  }
}
void main() {
  runApp(
    MaterialApp(
      home: Scaffold(
        body: Center(
          child: ShoppingListItem(
            product: const Product(name: 'Chips'),
            inCart: true,
            onCartChanged: (product, inCart) {},
          ),
        ),
      ),
    ),
  );
}
The ShoppingListItem widget follows a common pattern
for stateless widgets.  It stores the values it receives
in its constructor in final member variables,
which it then uses during its build() function.
For example, the inCart boolean toggles between two visual
appearances: one that uses the primary color from the current
theme, and another that uses gray.
When the user taps the list item, the widget doesn't modify
its inCart value directly. Instead, the widget calls the
onCartChanged function it received from its parent widget.
This pattern lets you store state higher in the widget
hierarchy, which causes the state to persist for longer periods of time.
In the extreme, the state stored on the widget passed to
runApp() persists for the lifetime of the
application.
When the parent receives the onCartChanged callback,
the parent updates its internal state, which triggers
the parent to rebuild and create a new instance
of ShoppingListItem with the new inCart value.
Although the parent creates a new instance of
ShoppingListItem when it rebuilds, that operation is cheap
because the framework compares the newly built widgets with the previously
built widgets and applies only the differences to the underlying
RenderObject.
Here's an example parent widget that stores mutable state:
code-excerpt "lib/main_shoppinglist.dart"?dartpad title="Flutter storing mutable state hands-on example in DartPad" run="true"
import 'package:flutter/material.dart';
class Product {
  const Product();
final String name;
}
typedef CartChangedCallback = Function(Product product, bool inCart);
class ShoppingListItem extends StatelessWidget {
  ShoppingListItem({
    required this.product,
    required this.inCart,
    required this.onCartChanged,
  }) : super(key: ObjectKey(product));
final Product product;
  final bool inCart;
  final CartChangedCallback onCartChanged;
Color _getColor(BuildContext context) {
    // The theme depends on the BuildContext because different
    // parts of the tree can have different themes.
    // The BuildContext indicates where the build is
    // taking place and therefore which theme to use.
return inCart //
    ? Colors.black54
    : Theme.of(context).primaryColor;
