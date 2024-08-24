For example, create a Text widget:
code-excerpt "layout/base/lib/main.dart (text)" replace="/child: //g"?
dart
Text('Hello World'),
Create an Image widget:
code-excerpt "layout/lakes/step5/lib/main.dart (image-asset)" remove="/width|height/"?
dart
return Image.asset(
  image,
  fit: BoxFit.cover,
);
Create an Icon widget:
code-excerpt "layout/lakes/step5/lib/main.dart (icon)"?
dart
Icon(
  Icons.star,
  color: Colors.red[500],
),
