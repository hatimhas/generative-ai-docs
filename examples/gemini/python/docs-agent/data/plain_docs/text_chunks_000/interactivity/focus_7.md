If you wish to listen for key events in a subtree,
set the onKeyEvent attribute of the Focus widget to
be a handler that either just listens to the key, or
handles the key and stops its propagation to other widgets.
Key events start at the focus node with primary focus.
If that node doesn't return KeyEventResult.handled from
its onKeyEvent handler, then its parent focus node is given the event.
If the parent doesn't handle it, it goes to its parent,
and so on, until it reaches the root of the focus tree.
If the event reaches the root of the focus tree without being handled, then
it is returned to the platform to give to
the next native control in the application
(in case the Flutter UI is part of a larger native application UI).
Events that are handled are not propagated to other Flutter widgets,
and they are also not propagated to native widgets.
Here's an example of a Focus widget that absorbs every key that
its subtree doesn't handle, without being able to be the primary focus:
code-excerpt "ui/advanced/focus/lib/samples.dart (absorb-keys)"?
dart
@override
Widget build(BuildContext context) {
  return Focus(
    onKeyEvent: (node, event) => KeyEventResult.handled,
    canRequestFocus: false,
    child: child,
  );
}
Focus key events are processed before text entry events, so handling a key event
when the focus widget surrounds a text field prevents that key from being
entered into the text field.
Here's an example of a widget that won't allow the letter "a" to be typed into
the text field:
code-excerpt "ui/advanced/focus/lib/samples.dart (no-letter-a)"?
dart
@override
Widget build(BuildContext context) {
  return Focus(
    onKeyEvent: (node, event) {
      return (event.logicalKey == LogicalKeyboardKey.keyA)
          ? KeyEventResult.handled
          : KeyEventResult.ignored;
    },
    child: const TextField(),
  );
}
If the intent is input validation, this example's functionality would probably
be better implemented using a TextInputFormatter, but the technique can still
be useful: the Shortcuts widget uses this method to handle shortcuts before
they become text input, for instance.
