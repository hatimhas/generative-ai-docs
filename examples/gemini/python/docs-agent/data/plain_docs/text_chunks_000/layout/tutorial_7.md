Add the following code after the TitleSection widget to contain the code
to build the row of buttons.
code-excerpt "lib/main.dart (button-start)"?
```dart
class ButtonSection extends StatelessWidget {
  const ButtonSection();
@override
  Widget build(BuildContext context) {
    final Color color = Theme.of(context).primaryColor;
    // ···
  }
}
```
