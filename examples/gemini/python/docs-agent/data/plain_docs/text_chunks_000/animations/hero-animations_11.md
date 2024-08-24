The RadialExpansion widget, the core of the demo, builds the
widget tree that clips the image during the transition.
The clipped shape results from the intersection of a circular clip
(that grows during flight),
with a rectangular clip (that remains a constant size throughout).
To do this, it builds the following widget tree:


  ![RadialExpansion widget tree](/assets/images/docs/ui/animations/radial-expansion-class.png)


Here's the code:
```dart
class RadialExpansion extends StatelessWidget {
  const RadialExpansion({
    super.key,
    required this.maxRadius,
    this.child,
  }) : [!clipRectSize = 2.0 * (maxRadius / math.sqrt2);!]
final double maxRadius;
  final clipRectSize;
  final Widget child;
@override
  Widget build(BuildContext context) {
    return [!ClipOval(!]
      child: [!Center(!]
        child: [!SizedBox(!]
          width: clipRectSize,
          height: clipRectSize,
          child: [!ClipRect(!]
            child: [!child,!] // Photo
          ),
        ),
      ),
    );
  }
}
```
Key information:

The hero wraps the RadialExpansion widget.
As the hero flies, its size changes and,
  because it constrains its child's size,
  the RadialExpansion widget changes size to match.
The RadialExpansion animation is created by two overlapping clips.
The example defines the tweening interpolation using
  MaterialRectCenterArcTween.
  The default flight path for a hero animation
  interpolates the tweens using the corners of the heroes.
  This approach affects the hero's aspect ratio during
  the radial transformation, so the new flight path uses
  MaterialRectCenterArcTween to interpolate the tweens using the
  center point of each hero.

Here's the code:
dart
  static RectTween _createRectTween(Rect? begin, Rect? end) {
    return MaterialRectCenterArcTween(begin: begin, end: end);
  }
The hero's flight path still follows an arc,
  but the image's aspect ratio remains constant.
