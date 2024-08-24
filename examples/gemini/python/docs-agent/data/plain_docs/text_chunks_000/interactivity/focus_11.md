Sometimes, it is useful to obtain the focus node of a Focus widget to
interrogate its attributes.
To access the focus node from an ancestor of the Focus widget, create and pass
in a FocusNode as the Focus widget's focusNode attribute. Because it needs
to be disposed of, the focus node you pass needs to be owned by a stateful
widget, so don't just create one each time it is built.
If you need access to the focus node from the descendant of a Focus widget,
you can call Focus.of(context) to obtain the focus node of the nearest Focuswidget to the given context. If you need to obtain the FocusNode of a Focus
widget within the same build function, use a Builder to make sure you have
the correct context. This is shown in the following example:
code-excerpt "ui/advanced/focus/lib/samples.dart (builder)"?
dart
@override
Widget build(BuildContext context) {
  return Focus(
    child: Builder(
      builder: (context) {
        final bool hasPrimary = Focus.of(context).hasPrimaryFocus;
        print('Building with primary focus: $hasPrimary');
        return const SizedBox(width: 100, height: 100);
      },
    ),
  );
}
