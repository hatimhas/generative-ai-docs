Add the following code as a separate widget after the ButtonSection widget.
code-excerpt "step4/lib/main.dart (text-section)"?
```dart
class TextSection extends StatelessWidget {
  const TextSection({
    super.key,
    required this.description,
  });
final String description;
@override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.all(32),
      child: Text(
        description,
        softWrap: true,
      ),
    );
  }
}
```
By setting softWrap to true, text lines fill the column width before
wrapping at a word boundary.
