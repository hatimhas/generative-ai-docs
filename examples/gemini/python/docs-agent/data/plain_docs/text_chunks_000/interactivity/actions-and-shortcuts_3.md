As you'll see below, actions are useful on their own, but the most common use
case involves binding them to a keyboard shortcut. This is what the Shortcuts
widget is for.
It is inserted into the widget hierarchy to define key combinations that
represent the user's intent when that key combination is pressed. To convert
that intended purpose for the key combination into a concrete action, the
Actions widget used to map the Intent to an Action. For instance, you can
define a SelectAllIntent, and bind it to your own SelectAllAction or to your
CanvasSelectAllAction, and from that one key binding, the system invokes
either one, depending on which part of your application has focus. Let's see how
the key binding part works:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (shortcuts)"?
dart
@override
Widget build(BuildContext context) {
  return Shortcuts(
    shortcuts: <LogicalKeySet, Intent>{
      LogicalKeySet(LogicalKeyboardKey.control, LogicalKeyboardKey.keyA):
          const SelectAllIntent(),
    },
    child: Actions(
      dispatcher: LoggingActionDispatcher(),
      actions: <Type, Action<Intent>>{
        SelectAllIntent: SelectAllAction(model),
      },
      child: Builder(
        builder: (context) => TextButton(
          onPressed: Actions.handler<SelectAllIntent>(
            context,
            const SelectAllIntent(),
          ),
          child: const Text('SELECT ALL'),
        ),
      ),
    ),
  );
}
The map given to a Shortcuts widget maps a LogicalKeySet (or a
ShortcutActivator, see note below) to an Intent instance. The logical key
set defines a set of one or more keys, and the intent indicates the intended
purpose of the keypress. The Shortcuts widget looks up key presses in the map,
to find an Intent instance, which it gives to the action's invoke() method.
:::note
ShortcutActivator is a replacement for LogicalKeySet.
It allows for more flexible and correct activation of shortcuts.
LogicalKeySet is a ShortcutActivator, of course, but
there is also SingleActivator, which takes a single key and the
optional modifiers to be pressed before the key.
Then there is CharacterActivator, which activates a shortcut based on the
character produced by a key sequence, instead of the logical keys themselves.
ShortcutActivator is also meant to be subclassed to allow for
custom ways of activating shortcuts from key events.
:::
