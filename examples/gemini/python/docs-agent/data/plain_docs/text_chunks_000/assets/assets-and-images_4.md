Your app can access its assets through an
AssetBundle object.
The two main methods on an asset bundle allow you to load a
string/text asset (loadString()) or an image/binary asset (load())
out of the bundle, given a logical key. The logical key maps to the path
to the asset specified in the pubspec.yaml file at build time.
