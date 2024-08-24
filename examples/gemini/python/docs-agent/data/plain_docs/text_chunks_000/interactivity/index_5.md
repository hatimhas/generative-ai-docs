The _FavoriteWidgetState class stores the mutable data
that can change over the lifetime of the widget.
When the app first launches, the UI displays a solid
red star, indicating that the lake has "favorite" status,
along with 41 likes. These values are stored in the
_isFavorited and _favoriteCount fields:
code-excerpt "lib/main.dart (favorite-state-fields)" replace="/(bool|int) .*/[!$&!]/g"?
dart
class _FavoriteWidgetState extends State<FavoriteWidget> {
  [!bool _isFavorited = true;!]
  [!int _favoriteCount = 41;!]
The class also defines a build() method,
which creates a row containing a red IconButton,
and Text.  You use IconButton (instead of Icon)
because it has an onPressed property that defines
the callback function (_toggleFavorite) for handling a tap.
You'll define the callback function next.
code-excerpt "lib/main.dart (favorite-state-build)" replace="/build|icon.*|onPressed.*|child: Text.*/[!$&!]/g"?
dart
class _FavoriteWidgetState extends State<FavoriteWidget> {
  // ···
  @override
  Widget [!build!](BuildContext context) {
    return Row(
      mainAxisSize: MainAxisSize.min,
      children: [
        Container(
          padding: const EdgeInsets.all(0),
          child: IconButton(
            padding: const EdgeInsets.all(0),
            alignment: Alignment.center,
            [!icon: (_isFavorited!]
                ? const Icon(Icons.star)
                : const Icon(Icons.star_border)),
            color: Colors.red[500],
            [!onPressed: _toggleFavorite,!]
          ),
        ),
        SizedBox(
          width: 18,
          child: SizedBox(
            [!child: Text('$_favoriteCount'),!]
          ),
        ),
      ],
    );
  }
  // ···
}
:::tip
Placing the Text in a SizedBox and setting its
width prevents a discernible "jump" when the text changes
between the values of 40 and 41 — a jump would
otherwise occur because those values have different widths.
:::
The _toggleFavorite() method, which is called when the
IconButton is pressed, calls setState().
Calling setState() is critical, because this
tells the framework that the widget's state has
changed and that the widget should be redrawn.
The function argument to setState() toggles the
UI between these two states:

A star icon and the number 41
A star_border icon and the number 40

code-excerpt "lib/main.dart (toggle-favorite)"?
dart
void _toggleFavorite() {
  setState(() {
    if (_isFavorited) {
      _favoriteCount -= 1;
      _isFavorited = false;
    } else {
      _favoriteCount += 1;
      _isFavorited = true;
    }
  });
}
