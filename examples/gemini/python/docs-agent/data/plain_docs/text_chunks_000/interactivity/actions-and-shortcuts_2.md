You also might wonder: why not just use a callback instead of an Action
object? The main reason is that it's useful for actions to decide whether they
are enabled by implementing isEnabled. Also, it is often helpful if the key
bindings, and the implementation of those bindings, are in different places.
If all you need are callbacks without the flexibility of Actions and
Shortcuts, you can use the CallbackShortcuts widget:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (callback-shortcuts)"?
dart
@override
Widget build(BuildContext context) {
  return CallbackShortcuts(
    bindings: <ShortcutActivator, VoidCallback>{
      const SingleActivator(LogicalKeyboardKey.arrowUp): () {
        setState(() => count = count + 1);
      },
      const SingleActivator(LogicalKeyboardKey.arrowDown): () {
        setState(() => count = count - 1);
      },
    },
    child: Focus(
      autofocus: true,
      child: Column(
        children: <Widget>[
          const Text('Press the up arrow key to add to the counter'),
          const Text('Press the down arrow key to subtract from the counter'),
          Text('count: $count'),
        ],
      ),
    ),
  );
}
