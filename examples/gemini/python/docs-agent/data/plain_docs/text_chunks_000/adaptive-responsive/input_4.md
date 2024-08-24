On desktop, it's common to change the mouse cursor
to indicate the functionality about the content the
mouse is hovering over. For example, you typically see
a hand cursor when you hover over a button,
or an I cursor when you hover over text.
Flutter's Material buttons handle basic focus states
for standard button and text cursors.
(A notable exception is if you change the default styling
of the Material buttons to set the overlayColor to transparent.)
Implement a focus state for any custom buttons or
gesture detectors in your app. 
If you change the default Material button styles,
test for keyboard focus states and 
implement your own, if needed.
To change the cursor from within your custom widgets,
use MouseRegion:
code-excerpt "lib/pages/focus_examples_page.dart (mouse-region)"?
dart
// Show hand cursor
return MouseRegion(
  cursor: SystemMouseCursors.click,
  // Request focus when clicked
  child: GestureDetector(
    onTap: () {
      Focus.of(context).requestFocus();
      _submit();
    },
    child: Logo(showBorder: hasFocus),
  ),
);
MouseRegion is also useful for creating custom
rollover and hover effects:
code-excerpt "lib/pages/focus_examples_page.dart (mouse-over)"?
dart
return MouseRegion(
  onEnter: (_) => setState(() => _isMouseOver = true),
  onExit: (_) => setState(() => _isMouseOver = false),
  onHover: (e) => print(e.localPosition),
  child: Container(
    height: 500,
    color: _isMouseOver ? Colors.blue : Colors.black,
  ),
);
For an example that changes the button style
to outline the button when it has focus,
check out the button code for the Wonderous app.
The app modifies the FocusNode.hasFocus
property to check whether the button has focus
and, if so, adds an outline.
