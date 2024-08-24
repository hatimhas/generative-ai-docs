Asset transformers can be chained and are applied in
the order they are declared.
Consider the following example using imaginary packages:
yaml
flutter:
  assets:
    - path: assets/bird.png
      transformers:
        - package: grayscale_filter
        - package: png_optimizer
Here, bird.png is transformed by the grayscale_filter package.
The output is then transformed by the png_optimizer package before being
bundled into the built app.
