To pass a string of arguments to an asset transformer,
also specify that in the pubspec:
yaml
flutter:
  assets:
    - path: assets/logo.svg
      transformers:
        - package: vector_graphics_compiler
          args: ['--tessellate', '--font-size=14']
