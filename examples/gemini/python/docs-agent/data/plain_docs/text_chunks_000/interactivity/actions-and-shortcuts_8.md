Most of the time, you just want to invoke an action, have it do its thing, and
forget about it. Sometimes, however, you might want to log the executed actions.
This is where replacing the default ActionDispatcher with a custom dispatcher
comes in.  You pass your ActionDispatcher to the Actions widget, and it
invokes actions from any Actions widgets below that one that doesn't set a
dispatcher of its own.
The first thing Actions does when invoking an action is look up the
ActionDispatcher and pass the action to it for invocation. If there is none,
it creates a default ActionDispatcher that simply invokes the action.
If you want a log of all the actions invoked, however, you can create your own
LoggingActionDispatcher to do the job:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (logging-action-dispatcher)"?
```dart
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
@override
  (bool, Object?) invokeActionIfEnabled(
    covariant Action action,
    covariant Intent intent, [
    BuildContext? context,
  ]) {
    print('Action invoked: $action($intent) from $context');
    return super.invokeActionIfEnabled(action, intent, context);
  }
}
```
Then you pass that to your top-level Actions widget:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (logging-action-dispatcher-usage)"?
dart
@override
Widget build(BuildContext context) {
  return Actions(
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
  );
}
This logs every action as it executes, like so:
console
flutter: Action invoked: SelectAllAction#906fc(SelectAllIntent#a98e3) from Builder(dependencies: _[ActionsMarker])
