To load an image from a package dependency,
the package argument must be provided to AssetImage.
For instance, suppose your application depends on a package
called my_icons, which has the following directory structure:
plaintext
.../pubspec.yaml
.../icons/heart.png
.../icons/1.5x/heart.png
.../icons/2.0x/heart.png
...etc.
To load the image, use:
code-excerpt "main.dart (package-image)"?
dart
return const AssetImage('icons/heart.png', package: 'my_icons');
Assets used by the package itself should also be fetched
using the package argument as above.
