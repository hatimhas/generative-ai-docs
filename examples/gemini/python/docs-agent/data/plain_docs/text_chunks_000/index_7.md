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
      title: Text(
        product.name,
        style: _getTextStyle(context),
      ),
    );
  }
}
class ShoppingList extends StatefulWidget {
  const ShoppingList();
final List products;
// The framework calls createState the first time
  // a widget appears at a given location in the tree.
  // If the parent rebuilds and uses the same type of
  // widget (with the same key), the framework re-uses
  // the State object instead of creating a new State object.
@override
  State createState() => _ShoppingListState();
}
class _ShoppingListState extends State {
  final _shoppingCart = {};
void _handleCartChanged(Product product, bool inCart) {
    setState(() {
      // When a user changes what's in the cart, you need
      // to change _shoppingCart inside a setState call to
      // trigger a rebuild.
      // The framework then calls build, below,
      // which updates the visual appearance of the app.
  if (!inCart) {
    _shoppingCart.add(product);
  } else {
    _shoppingCart.remove(product);
  }
});
}
@override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Shopping List'),
      ),
      body: ListView(
        padding: const EdgeInsets.symmetric(vertical: 8),
        children: widget.products.map((product) {
          return ShoppingListItem(
            product: product,
            inCart: _shoppingCart.contains(product),
            onCartChanged: _handleCartChanged,
          );
        }).toList(),
      ),
    );
  }
}
void main() {
  runApp(const MaterialApp(
    title: 'Shopping App',
    home: ShoppingList(
      products: [
        Product(name: 'Eggs'),
        Product(name: 'Flour'),
        Product(name: 'Chocolate chips'),
      ],
    ),
  ));
}
```
The ShoppingList class extends StatefulWidget,
which means this widget stores mutable state.
When the ShoppingList widget is first inserted
into the tree, the framework calls the createState() function
to create a fresh instance of _ShoppingListState to associate with that
location in the tree. (Notice that subclasses of
State are typically named with leading underscores to
indicate that they are private implementation details.)
When this widget's parent rebuilds, the parent creates a new instance
of ShoppingList, but the framework reuses the _ShoppingListState
instance that is already in the tree rather than calling
createState again.
To access properties of the current ShoppingList,
the _ShoppingListState can use its widget property.
If the parent rebuilds and creates a new ShoppingList,
the _ShoppingListState rebuilds with the new widget value.
If you wish to be notified when the widget property changes,
override the didUpdateWidget() function, which is passed
an oldWidget to let you compare the old widget with
the current widget.
When handling the onCartChanged callback, the _ShoppingListState
mutates its internal state by either adding or removing a product from
_shoppingCart. To signal to the framework that it changed its internal
state, it wraps those calls in a setState() call.
Calling setState marks this widget as dirty and schedules it to be rebuilt
the next time your app needs to update the screen.
If you forget to call setState when modifying the internal
state of a widget, the framework won't know your widget is
dirty and might not call the widget's build() function,
which means the user interface might not update to reflect
the changed state.  By managing state in this way,
you don't need to write separate code for creating and
updating child widgets. Instead, you simply implement the build
function, which handles both situations.
