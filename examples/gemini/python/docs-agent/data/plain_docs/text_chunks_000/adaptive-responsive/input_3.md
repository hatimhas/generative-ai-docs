In addition to tab traversal, desktop and web users are accustomed
to having various keyboard shortcuts bound to specific actions.
Whether it's the Delete key for quick deletions or
Control+N for a new document, be sure to consider the different
accelerators your users expect. The keyboard is a powerful
input tool, so try to squeeze as much efficiency from it as you can.
Your users will appreciate it!
Keyboard accelerators can be accomplished in a few ways in Flutter,
depending on your goals.
If you have a single widget like a TextField or a Button that
already has a focus node, you can wrap it in a KeyboardListener
or a Focus widget and listen for keyboard events:
code-excerpt "lib/pages/focus_examples_page.dart (focus-keyboard-listener)"?
dart
  @override
  Widget build(BuildContext context) {
    return Focus(
      onKeyEvent: (node, event) {
        if (event is KeyDownEvent) {
          print(event.logicalKey);
        }
        return KeyEventResult.ignored;
      },
      child: ConstrainedBox(
        constraints: const BoxConstraints(maxWidth: 400),
        child: const TextField(
          decoration: InputDecoration(
            border: OutlineInputBorder(),
          ),
        ),
      ),
    );
  }
}
To apply a set of keyboard shortcuts to a large section
of the tree, use the Shortcuts widget:
code-excerpt "lib/widgets/extra_widget_excerpts.dart (shortcuts)"?
```dart
// Define a class for each type of shortcut action you want
class CreateNewItemIntent extends Intent {
  const CreateNewItemIntent();
}
Widget build(BuildContext context) {
  return Shortcuts(
    // Bind intents to key combinations
    shortcuts: const {
      SingleActivator(LogicalKeyboardKey.keyN, control: true):
          CreateNewItemIntent(),
    },
    child: Actions(
      // Bind intents to an actual method in your code
      actions: >{
        CreateNewItemIntent: CallbackAction(
          onInvoke: (intent) => _createNewItem(),
        ),
      },
      // Your sub-tree must be wrapped in a focusNode, so it can take focus.
      child: Focus(
        autofocus: true,
        child: Container(),
      ),
    ),
  );
}
```
The Shortcuts widget is useful because it only
allows shortcuts to be fired when this widget tree
or one of its children has focus and is visible.
The final option is a global listener. This listener
can be used for always-on, app-wide shortcuts or for
panels that can accept shortcuts whenever they're visible
(regardless of their focus state). Adding global listeners
is easy with HardwareKeyboard:
code-excerpt "lib/widgets/extra_widget_excerpts.dart (hardware-keyboard)"?
```dart
@override
void initState() {
  super.initState();
  HardwareKeyboard.instance.addHandler(_handleKey);
}
@override
void dispose() {
  HardwareKeyboard.instance.removeHandler(_handleKey);
  super.dispose();
}
```
To check key combinations with the global listener,
you can use the HardwareKeyboard.instance.logicalKeysPressed set.
For example, a method like the following can check whether any
of the provided keys are being held down:
code-excerpt "lib/widgets/extra_widget_excerpts.dart (keys-pressed)"?
dart
static bool isKeyDown(Set<LogicalKeyboardKey> keys) {
  return keys
      .intersection(HardwareKeyboard.instance.logicalKeysPressed)
      .isNotEmpty;
}
Putting these two things together,
you can fire an action when Shift+N is pressed:
code-excerpt "lib/widgets/extra_widget_excerpts.dart (handle-key)"?
```dart
bool _handleKey(KeyEvent event) {
  bool isShiftDown = isKeyDown({
    LogicalKeyboardKey.shiftLeft,
    LogicalKeyboardKey.shiftRight,
  });
if (isShiftDown && event.logicalKey == LogicalKeyboardKey.keyN) {
    _createNewItem();
    return true;
  }
return false;
}
```
One note of caution when using the static listener,
is that you often need to disable it when the user
is typing in a field or when the widget it's
associated with is hidden from view.
Unlike with Shortcuts or KeyboardListener,
this is your responsibility to manage. This can be especially
important when you're binding a Delete/Backspace accelerator for
Delete, but then have child TextFields that the user
might be typing in.
