If the desired asset is specified in the pubspec.yaml
file of the package, it's bundled automatically with the
application. In particular, assets used by the package
itself must be specified in its pubspec.yaml.
A package can also choose to have assets in its lib/
folder that are not specified in its pubspec.yaml file.
In this case, for those images to be bundled,
the application has to specify which ones to include in its
pubspec.yaml. For instance, a package named fancy_backgrounds
could have the following files:
plaintext
.../lib/backgrounds/background1.png
.../lib/backgrounds/background2.png
.../lib/backgrounds/background3.png
To include, say, the first image, the pubspec.yaml of the
application should specify it in the assets section:
yaml
flutter:
  assets:
    - packages/fancy_backgrounds/backgrounds/background1.png
The lib/ is implied,
so it should not be included in the asset path.
If you are developing a package, to load an asset within the package, specify it in the pubspec.yaml of the package:
yaml
flutter:
  assets:
    - assets/images/
To load the image within your package, use:
dart
return const AssetImage('packages/fancy_backgrounds/backgrounds/background1.png');
