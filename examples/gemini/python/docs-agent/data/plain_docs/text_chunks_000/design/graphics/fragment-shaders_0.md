:::note
Both the Skia and Impeller backends support writing a
custom shader. Except where noted, the same
instructions apply to both.
:::
Custom shaders can be used to provide rich graphical effects
beyond those provided by the Flutter SDK.
A shader is a program authored in a small,
Dart-like language, known as GLSL,
and executed on the user's GPU.
Custom shaders are added to a Flutter project
by listing them in the pubspec.yaml file,
and obtained using the FragmentProgram API.
Shaders, in the form of GLSL files with the .frag extension,
must be declared in the shaders section of your project's pubspec.yaml file.
The Flutter command-line tool compiles the shader
to its appropriate backend format,
and generates its necessary runtime metadata.
The compiled shader is then included in the application just like an asset.
yaml
flutter:
  shaders:
    - shaders/myshader.frag
When running in debug mode,
changes to a shader program trigger recompilation
and update the shader during hot reload or hot restart.
Shaders from packages are added to a project
with packages/$pkgname prefixed to the shader program's name
(where $pkgname is the name of the package).
