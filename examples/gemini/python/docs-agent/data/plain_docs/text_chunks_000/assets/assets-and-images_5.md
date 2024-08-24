Each Flutter app has a rootBundle
object for easy access to the main asset bundle.
It is possible to load assets directly using the
rootBundle global static from
package:flutter/services.dart.
However, it's recommended to obtain the AssetBundle
for the current BuildContext using
DefaultAssetBundle, rather than the default
asset bundle that was built with the app; this
approach enables a parent widget to substitute a
different AssetBundle at run time,
which can be useful for localization or testing
scenarios.
Typically, you'll use DefaultAssetBundle.of()
to indirectly load an asset, for example a JSON file,
from the app's runtime rootBundle.

  Need example here to show obtaining the AssetBundle for the current
  BuildContext using DefaultAssetBundle.of

Outside of a Widget context, or when a handle
to an AssetBundle is not available,
you can use rootBundle to directly load such assets.
For example:
code-excerpt "main.dart (root-bundle-load)"?
```dart
import 'package:flutter/services.dart' show rootBundle;
Future loadAsset() async {
  return await rootBundle.loadString('assets/config.json');
}
```
