You only need to specify the main asset or its parent directory
in the assets section of pubspec.yaml.
Flutter bundles the variants for you.
Each entry should correspond to a real file, with the exception of
the main asset entry. If the main asset entry doesn't correspond
to a real file, then the asset with the lowest resolution
is used as the fallback for devices with device pixel
ratios below that resolution. The entry should still
be included in the pubspec.yaml manifest, however.
Anything using the default asset bundle inherits resolution
awareness when loading images. (If you work with some of the lower
level classes, like ImageStream or ImageCache,
you'll also notice parameters related to scale.)
