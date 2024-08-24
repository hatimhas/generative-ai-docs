The shortcut manager, a longer-lived object than the Shortcuts widget, passes
on key events when it receives them. It contains the logic for deciding how to
handle the keys, the logic for walking up the tree to find other shortcut
mappings, and maintains a map of key combinations to intents.
While the default behavior of the ShortcutManager is usually desirable, the
Shortcuts widget takes a ShortcutManager that you can subclass to customize
its functionality.
For example, if you wanted to log each key that a Shortcuts widget handled,
you could make a LoggingShortcutManager:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (logging-shortcut-manager)"?
dart
class LoggingShortcutManager extends ShortcutManager {
  @override
  KeyEventResult handleKeypress(BuildContext context, KeyEvent event) {
    final KeyEventResult result = super.handleKeypress(context, event);
    if (result == KeyEventResult.handled) {
      print('Handled shortcut $event in $context');
    }
    return result;
  }
}
Now, every time the Shortcuts widget handles a shortcut, it prints out the key
event and relevant context.
