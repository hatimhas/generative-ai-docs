Add the following code into the ButtonSection widget.

Add three instances of the ButtonWithText widget, once for each button.
Pass the color, Icon, and text for that specific button.
Align the columns along the main axis with the
   MainAxisAlignment.spaceEvenly value.
   The main axis for a Row widget is horizontal and the main axis for a
   Column widget is vertical.
   This value, then, tells Flutter to arrange the free space in equal amounts
   before, between, and after each column along the Row.

code-excerpt "lib/main.dart (button-section)"?
```dart
class ButtonSection extends StatelessWidget {
  const ButtonSection();
@override
  Widget build(BuildContext context) {
    final Color color = Theme.of(context).primaryColor;
    return SizedBox(
      child: Row(
        mainAxisAlignment: MainAxisAlignment.spaceEvenly,
        children: [
          ButtonWithText(
            color: color,
            icon: Icons.call,
            label: 'CALL',
          ),
          ButtonWithText(
            color: color,
            icon: Icons.near_me,
            label: 'ROUTE',
          ),
          ButtonWithText(
            color: color,
            icon: Icons.share,
            label: 'SHARE',
          ),
        ],
      ),
    );
  }
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
// ···
    );
  }
}
```
