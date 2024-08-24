code-excerpt path-base="ui/assets_and_images/lib"?
Flutter apps can include both code and assets
(sometimes called resources). An asset is a file
that is bundled and deployed with your app,
and is accessible at runtime. Common types of assets include
static data (for example, JSON files),
configuration files, icons, and images
(JPEG, WebP, GIF, animated WebP/GIF, PNG, BMP, and WBMP).
Flutter uses the pubspec.yaml file,
located at the root of your project,
to identify assets required by an app.
Here is an example:
yaml
flutter:
  assets:
    - assets/my_icon.png
    - assets/background.png
To include all assets under a directory,
specify the directory name with the / character at the end:
yaml
flutter:
  assets:
    - directory/
    - directory/subdirectory/
:::note
Only files located directly in the directory are included.
Resolution-aware asset image variants are the only exception.
To add files located in subdirectories, create an entry per directory.
:::
