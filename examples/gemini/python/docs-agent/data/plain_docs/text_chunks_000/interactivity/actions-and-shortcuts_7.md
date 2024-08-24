The actions system has several ways to invoke actions.  By far the most common
way is through the use of a Shortcuts widget covered in the previous section,
but there are other ways to interrogate the actions subsystem and invoke an
action. It's possible to invoke actions that are not bound to keys.
For instance, to find an action associated with an intent, you can use:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (maybe-find)"?
dart
Action<SelectAllIntent>? selectAll =
    Actions.maybeFind<SelectAllIntent>(context);
This returns an Action associated with the SelectAllIntent type if one is
available in the given context.  If one isn't available, it returns null. If
an associated Action should always be available, then use find instead of
maybeFind, which throws an exception when it doesn't find a matching Intent
type.
To invoke the action (if it exists), call:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (invoke-action)"?
dart
Object? result;
if (selectAll != null) {
  result =
      Actions.of(context).invokeAction(selectAll, const SelectAllIntent());
}
Combine that into one call with the following:
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (maybe-invoke)"?
dart
Object? result =
    Actions.maybeInvoke<SelectAllIntent>(context, const SelectAllIntent());
Sometimes you want to invoke an action as a
result of pressing a button or another control.
You can do this with the Actions.handler function.
If the intent has a mapping to an enabled action,
the Actions.handler function creates a handler closure.
However, if it doesn't have a mapping, it returns null.
This allows the button to be disabled if
there is no enabled action that matches in the context.
code-excerpt "ui/advanced/actions_and_shortcuts/lib/samples.dart (handler)"?
dart
@override
Widget build(BuildContext context) {
  return Actions(
    actions: <Type, Action<Intent>>{
      SelectAllIntent: SelectAllAction(model),
    },
    child: Builder(
      builder: (context) => TextButton(
        onPressed: Actions.handler<SelectAllIntent>(
          context,
          SelectAllIntent(controller: controller),
        ),
        child: const Text('SELECT ALL'),
      ),
    ),
  );
}
The Actions widget only invokes actions when isEnabled(Intent intent)
returns true, allowing the action to decide if the dispatcher should consider it
for invocation.  If the action isn't enabled, then the Actions widget gives
another enabled action higher in the widget hierarchy (if it exists) a chance to
execute.
The previous example uses a Builder because Actions.handler and
Actions.invoke (for example) only finds actions in the provided context, and
if the example passes the context given to the build function, the framework
starts looking above the current widget.  Using a Builder allows the
framework to find the actions defined in the same build function.
You can invoke an action without needing a BuildContext, but since the
Actions widget requires a context to find an enabled action to invoke, you
need to provide one, either by creating your own Action instance, or by
finding one in an appropriate context with Actions.find.
To invoke the action, pass the action to the invoke method on an
ActionDispatcher, either one you created yourself, or one retrieved from an
existing Actions widget using the Actions.of(context) method. Check whether
the action is enabled before calling invoke. Of course, you can also just call
invoke on the action itself, passing an Intent, but then you opt out of any
services that an action dispatcher might provide (like logging, undo/redo, and
so on).
