Actions, in their simplest form, are just subclasses of Action<Intent> with an
invoke() method. Here's a simple action that simply invokes a function on the
provided model:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (select-all-action)"?
```dart
class SelectAllAction extends Action {
  SelectAllAction(this.model);
final Model model;
@override
  void invoke(covariant SelectAllIntent intent) => model.selectAll();
}
```
Or, if it's too much of a bother to create a new class, use a CallbackAction:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (callback-action)"?
dart
CallbackAction(onInvoke: (intent) => model.selectAll());
Once you have an action, you add it to your application using the Actions
widget, which takes a map of Intent types to Actions:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (select-all-usage)"?
dart
@override
Widget build(BuildContext context) {
  return Actions(
    actions: <Type, Action<Intent>>{
      SelectAllIntent: SelectAllAction(model),
    },
    child: child,
  );
}
The Shortcuts widget uses the Focus widget's context and Actions.invoke to
find which action to invoke. If the Shortcuts widget doesn't find a matching
intent type in the first Actions widget encountered, it considers the next
ancestor Actions widget, and so on, until it reaches the root of the widget
tree, or finds a matching intent type and invokes the corresponding action.
