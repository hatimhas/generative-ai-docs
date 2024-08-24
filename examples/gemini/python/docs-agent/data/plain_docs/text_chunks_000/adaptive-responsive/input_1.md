Users with physical keyboards expect that they can use
the tab key to quickly navigate an application,
and users with motor or vision differences often rely
completely on keyboard navigation.
There are two considerations for tab interactions:
how focus moves from widget to widget, known as traversal,
and the visual highlight shown when a widget is focused.
Most built-in components, like buttons and text fields,
support traversal and highlights by default.
If you have your own widget that you want included in
traversal, you can use the FocusableActionDetector widget
to create your own controls. The FocusableActionDetector
widget is helpful for combining focus, mouse input,
and shortcuts together in one widget. You can create
a detector that defines actions and key bindings,
and provides callbacks for handling focus and hover highlights.
code-excerpt "lib/pages/focus_examples_page.dart (focusable-action-detector)"?
dart
class _BasicActionDetectorState extends State<BasicActionDetector> {
  bool _hasFocus = false;
  @override
  Widget build(BuildContext context) {
    return FocusableActionDetector(
      onFocusChange: (value) => setState(() => _hasFocus = value),
      actions: <Type, Action<Intent>>{
        ActivateIntent: CallbackAction<Intent>(onInvoke: (intent) {
          print('Enter or Space was pressed!');
          return null;
        }),
      },
      child: Stack(
        clipBehavior: Clip.none,
        children: [
          const FlutterLogo(size: 100),
          // Position focus in the negative margin for a cool effect
          if (_hasFocus)
            Positioned(
              left: -4,
              top: -4,
              bottom: -4,
              right: -4,
              child: _roundedBorder(),
            )
        ],
      ),
    );
  }
}
