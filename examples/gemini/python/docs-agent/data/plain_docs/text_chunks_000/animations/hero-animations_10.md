The Photo class builds the widget tree that holds the image:
```dart
class Photo extends StatelessWidget {
  const Photo();
final String photo;
  final Color? color;
  final VoidCallback onTap;
Widget build(BuildContext context) {
    return [!Material(!]
      // Slightly opaque color appears where the image has transparency.
      [!color: Theme.of(context).primaryColor.withOpacity(0.25),!]
      child: [!InkWell(!]
        onTap: [!onTap,!]
        child: [!Image.asset(!]
          photo,
          fit: BoxFit.contain,
        ),
      ),
    );
  }
}
```
Key information:

The InkWell captures the tap gesture.
  The calling function passes the onTap() function to the
  Photo's constructor.
During flight, the InkWell draws its splash on its first
  Material ancestor.
The Material widget has a slightly opaque color, so the
  transparent portions of the image are rendered with color.
  This ensures that the circle-to-square transition is easy to see,
  even for images with transparency.
The Photo class does not include the Hero in its widget tree.
  For the animation to work, the hero
  wraps the RadialExpansion widget.
