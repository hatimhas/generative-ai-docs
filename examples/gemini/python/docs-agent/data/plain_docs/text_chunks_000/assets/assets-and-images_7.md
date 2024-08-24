Flutter can load resolution-appropriate images for
the current device pixel ratio.
AssetImage will map a logical requested
asset onto one that most closely matches the current
device pixel ratio.
For this mapping to work, assets should be arranged
according to a particular directory structure:
plaintext
.../image.png
.../Mx/image.png
.../Nx/image.png
...etc.
Where M and N are numeric identifiers that correspond
to the nominal resolution of the images contained within.
In other words, they specify the device pixel ratio that
the images are intended for.
In this example, image.png is considered the main asset,
while Mx/image.png and Nx/image.png are considered to be
variants.
The main asset is assumed to correspond to a resolution of 1.0.
For example, consider the following asset layout for an
image named my_icon.png:
plaintext
.../my_icon.png       (mdpi baseline)
.../1.5x/my_icon.png  (hdpi)
.../2.0x/my_icon.png  (xhdpi)
.../3.0x/my_icon.png  (xxhdpi)
.../4.0x/my_icon.png  (xxxhdpi)
On devices with a device pixel ratio of 1.8, the asset
.../2.0x/my_icon.png is chosen.
For a device pixel ratio of 2.7, the asset
.../3.0x/my_icon.png is chosen.
If the width and height of the rendered image are not specified
on the Image widget, the nominal resolution is used to scale
the asset so that it occupies the same amount of screen space
as the main asset would have, just with a higher resolution.
That is, if .../my_icon.png is 72px by 72px, then
.../3.0x/my_icon.png should be 216px by 216px;
but they both render into 72px by 72px (in logical pixels),
if width and height are not specified.
:::note
Device pixel ratio depends on MediaQueryData.size, which requires having either
MaterialApp or CupertinoApp as an ancestor of your AssetImage.
:::
