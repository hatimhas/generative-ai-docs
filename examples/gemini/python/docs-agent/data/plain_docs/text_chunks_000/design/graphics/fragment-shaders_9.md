uniform vec2 uSize;
uniform sampler2D uTexture;
out vec4 fragColor;
void main() {
  vec2 uv = FlutterFragCoord().xy / uSize;
  fragColor = texture(uTexture, uv);
}
```
By default, the image uses
TileMode.clamp to determine how values outside
of the range of [0, 1] behave.
Customization of the tile mode is not
supported and needs to be emulated in the shader.
