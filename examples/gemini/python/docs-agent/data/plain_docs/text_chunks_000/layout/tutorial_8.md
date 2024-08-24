As the code for each column could use the same syntax,
create a widget named ButtonWithText.
The widget's constructor accepts a color, icon data, and a label for the button.
Using these values, the widget builds a Column with an Icon and a stylized
Text widget as its children.
To help separate these children, a Padding widget the Text widget
is wrapped with a Padding widget.
Add the following code after the ButtonSection class.
code-excerpt "lib/main.dart (button-with-text)"?
```dart
class ButtonSection extends StatelessWidget {
  const ButtonSection();
// ···
}
class ButtonWithText extends StatelessWidget {
  const ButtonWithText({
    super.key,
    required this.color,
    required this.icon,
    required this.label,
  });
final Color color;
  final IconData icon;
  final String label;
@override
  Widget build(BuildContext context) {
    return Column(
      mainAxisSize: MainAxisSize.min,
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        Icon(icon, color: color),
        Padding(
          padding: const EdgeInsets.only(top: 8),
          child: Text(
            label,
            style: TextStyle(
              fontSize: 12,
              fontWeight: FontWeight.w400,
              color: color,
            ),
          ),
        ),
      ],
    );
  }
```
