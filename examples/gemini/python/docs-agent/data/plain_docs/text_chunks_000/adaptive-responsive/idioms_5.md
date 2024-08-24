Dealing with multi-select within a list is another area
with subtle differences across platforms:
code-excerpt "lib/widgets/extra_widget_excerpts.dart (multi-select-shift)"?
dart
static bool get isSpanSelectModifierDown =>
    isKeyDown();
To perform a platform-aware check for control or command,
you can write something like this:
code-excerpt "lib/widgets/extra_widget_excerpts.dart (multi-select-modifier-down)"?
dart
static bool get isMultiSelectModifierDown {
  bool isDown = false;
  if (Platform.isMacOS) {
    isDown = isKeyDown(
      ,
    );
  } else {
    isDown = isKeyDown(
      ,
    );
  }
  return isDown;
}
A final consideration for keyboard users is the Select All action.
If you have a large list of items of selectable items,
many of your keyboard users will expect that they can use
Control+A to select all the items.
