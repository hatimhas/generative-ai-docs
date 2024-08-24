On Android the assets are available through the
AssetManager API.  The lookup key used in,
for instance openFd, is obtained from
lookupKeyForAsset on PluginRegistry.Registrar or
getLookupKeyForAsset on FlutterView.
PluginRegistry.Registrar is available when developing a plugin
while FlutterView would be the choice when developing an
app including a platform view.
As an example, suppose you have specified the following
in your pubspec.yaml
yaml
flutter:
  assets:
    - icons/heart.png
This reflects the following structure in your Flutter app.
plaintext
.../pubspec.yaml
.../icons/heart.png
...etc.
To access icons/heart.png from your Java plugin code,
do the following:
java
AssetManager assetManager = registrar.context().getAssets();
String key = registrar.lookupKeyForAsset("icons/heart.png");
AssetFileDescriptor fd = assetManager.openFd(key);
