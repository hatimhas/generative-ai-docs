There isn't a built-in data type for colors.
Instead they are commonly represented as a vec4
with each component corresponding to one of the RGBA
color channels.
The single output fragColor expects that the color value
is normalized to be in the range of 0.0 to 1.0
and that it has premultiplied alpha.
This is different than typical Flutter colors which use
a 0-255 value encoding and have unpremultipled alpha.
