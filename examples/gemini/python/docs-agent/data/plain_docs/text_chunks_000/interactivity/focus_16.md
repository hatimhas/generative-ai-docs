The FocusTraversalGroup widget should be placed in the tree around widget
subtrees that should be fully traversed before moving on to another widget or
group of widgets. Just grouping widgets into related groups is often enough to
resolve many tab traversal ordering problems. If not, the group can also be
given a FocusTraversalPolicy to determine the ordering within the group.
The default ReadingOrderTraversalPolicy is usually sufficient, but in
cases where more control over ordering is needed, an
OrderedTraversalPolicy can be used. The order argument of the
FocusTraversalOrder widget wrapped around the focusable components
determines the order. The order can be any subclass of FocusOrder, but
NumericFocusOrder and LexicalFocusOrder are provided.
If none of the provided focus traversal policies are sufficient for your
application, you could also write your own policy and use it to determine any
custom ordering you want.
Here's an example of how to use the FocusTraversalOrder widget to traverse a
row of buttons in the order TWO, ONE, THREE using NumericFocusOrder.
code-excerpt "ui/advanced/focus/lib/samples.dart (ordered-button-row)"?
```dart
class OrderedButtonRow extends StatelessWidget {
  const OrderedButtonRow();
@override
  Widget build(BuildContext context) {
    return FocusTraversalGroup(
      policy: OrderedTraversalPolicy(),
      child: Row(
        children: [
          const Spacer(),
          FocusTraversalOrder(
            order: const NumericFocusOrder(2),
            child: TextButton(
              child: const Text('ONE'),
              onPressed: () {},
            ),
          ),
          const Spacer(),
          FocusTraversalOrder(
            order: const NumericFocusOrder(1),
            child: TextButton(
              child: const Text('TWO'),
              onPressed: () {},
            ),
          ),
          const Spacer(),
          FocusTraversalOrder(
            order: const NumericFocusOrder(3),
            child: TextButton(
              child: const Text('THREE'),
              onPressed: () {},
            ),
          ),
          const Spacer(),
        ],
      ),
    );
  }
}
```
