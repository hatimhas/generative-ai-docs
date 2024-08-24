The combination of Actions and Shortcuts is powerful: you can define generic
intents that map to specific actions at the widget level. Here's a simple app
that illustrates the concepts described above. The app creates a text field that
also has "select all" and "copy to clipboard" buttons next to it. The buttons
invoke actions to accomplish their work. All the invoked actions and
shortcuts are logged.
code-excerpt "ui/advanced/actions_and_shortcuts/lib/copyable_text.dart"?
```dartpad title="Copyable text DartPad hands-on example" run="true"
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
/// A text field that also has buttons to select all the text and copy the
/// selected text to the clipboard.
class CopyableTextField extends StatefulWidget {
  const CopyableTextField();
final String title;
@override
  State createState() => _CopyableTextFieldState();
}
class _CopyableTextFieldState extends State {
  late final TextEditingController controller = TextEditingController();
@override
  void dispose() {
    controller.dispose();
    super.dispose();
  }
@override
  Widget build(BuildContext context) {
    return Actions(
      dispatcher: LoggingActionDispatcher(),
      actions: >{
        ClearIntent: ClearAction(controller),
        CopyIntent: CopyAction(controller),
        SelectAllIntent: SelectAllAction(controller),
      },
      child: Builder(builder: (context) {
        return Scaffold(
          body: Center(
            child: Row(
              children: [
                const Spacer(),
                Expanded(
                  child: TextField(controller: controller),
                ),
                IconButton(
                  icon: const Icon(Icons.copy),
                  onPressed:
                      Actions.handler(context, const CopyIntent()),
                ),
                IconButton(
                  icon: const Icon(Icons.select_all),
                  onPressed: Actions.handler(
                      context, const SelectAllIntent()),
                ),
                const Spacer(),
              ],
            ),
          ),
        );
      }),
    );
  }
}
/// A ShortcutManager that logs all keys that it handles.
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
/// An ActionDispatcher that logs all the actions that it invokes.
class LoggingActionDispatcher extends ActionDispatcher {
  @override
  Object? invokeAction(
    covariant Action action,
    covariant Intent intent, [
    BuildContext? context,
  ]) {
    print('Action invoked: $action($intent) from $context');
    super.invokeAction(action, intent, context);
return null;
}
}
/// An intent that is bound to ClearAction in order to clear its
