Define the following ImageSection widget after the other declarations.
code-excerpt "step5/lib/main.dart (image-section)"?
```dart
class ImageSection extends StatelessWidget {
  const ImageSection();
final String image;
@override
  Widget build(BuildContext context) {
    return Image.asset(
      image,
      width: 600,
      height: 240,
      fit: BoxFit.cover,
    );
  }
}
```
The BoxFit.cover value tells Flutter to display the image with
two constraints. First, display the image as small as possible.
Second, cover all the space that the layout allotted, called the render box.
