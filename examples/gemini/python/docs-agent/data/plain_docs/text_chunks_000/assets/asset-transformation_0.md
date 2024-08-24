You can configure your project to automatically transform assets
at build time using compatible Dart packages.
In the pubspec.yaml file, list the assets to be transformed and the associated
transformer package.
yaml
flutter:
  assets:
    - path: assets/logo.svg
      transformers:
        - package: vector_graphics_compiler
With this configuration, assets/logo.svg is transformed by the
vector_graphics_compiler package as it is copied to the build output. This
package precompiles SVG files into an optimized binary files that can be
displayed using the vector_graphics package, like so:
code-excerpt "ui/assets_and_images/lib/logo.dart (TransformedAsset)"?
```dart
import 'package:vector_graphics/vector_graphics.dart';
const Widget logo = VectorGraphic(
  loader: AssetBytesLoader('assets/logo.svg'),
);
```
