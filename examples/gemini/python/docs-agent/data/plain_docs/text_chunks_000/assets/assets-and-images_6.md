To load an image, use the AssetImage
class in a widget's build() method.
For example, your app can load the background
image from the asset declarations in the previous example:
code-excerpt "main.dart (background-image)"?
dart
return const Image(image: AssetImage('assets/background.png'));
