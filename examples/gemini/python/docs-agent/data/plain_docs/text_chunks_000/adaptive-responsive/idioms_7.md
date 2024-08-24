A common expectation on the web (and to a lesser extent desktop)
is that most visible text can be selected with the mouse cursor.
When text is not selectable,
users on the web tend to have an adverse reaction.
Luckily, this is easy to support with the SelectableText widget:
code-excerpt "lib/widgets/extra_widget_excerpts.dart (selectable-text)"?
dart
return const SelectableText('Select me!');
To support rich text, then use TextSpan:
code-excerpt "lib/widgets/extra_widget_excerpts.dart (rich-text-span)"?
dart
return const SelectableText.rich(
  TextSpan(
    children: [
      TextSpan(text: 'Hello'),
      TextSpan(text: 'Bold', style: TextStyle(fontWeight: FontWeight.bold)),
    ],
  ),
);
