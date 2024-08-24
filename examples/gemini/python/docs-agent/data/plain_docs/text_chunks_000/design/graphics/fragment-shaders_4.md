A fragment program can be configured by defining
uniform values in the GLSL shader source
and then setting these values in Dart for
each fragment shader instance.
Floating point uniforms with the GLSL types
float, vec2, vec3, and vec4
are set using the FragmentShader.setFloat method.
GLSL sampler values, which use the sampler2D type,
are set using the FragmentShader.setImageSampler method.
The correct index for each uniform value is determined by the order
that the uniform values are defined in the fragment program.
For data types composed of multiple floats, such as a vec4,
you must call FragmentShader.setFloat once for each value.
For example, given the following uniforms declarations in a GLSL fragment program:
glsl
uniform float uScale;
uniform sampler2D uTexture;
uniform vec2 uMagnitude;
uniform vec4 uColor;
The corresponding Dart code to initialize these uniform values is as follows:
```dart
void updateShader(FragmentShader shader, Color color, Image image) {
  shader.setFloat(0, 23);  // uScale
  shader.setFloat(1, 114); // uMagnitude x
  shader.setFloat(2, 83);  // uMagnitude y
// Convert color to premultiplied opacity.
  shader.setFloat(3, color.red / 255 * color.opacity);   // uColor r
  shader.setFloat(4, color.green / 255 * color.opacity); // uColor g
  shader.setFloat(5, color.blue / 255 * color.opacity);  // uColor b
  shader.setFloat(6, color.opacity);                     // uColor a
// Initialize sampler uniform.
  shader.setImageSampler(0, image);
 }
 ```
Observe that the indices used with FragmentShader.setFloat
do not count the sampler2D uniform.
This uniform is set separately with FragmentShader.setImageSampler,
with the index starting over at 0.
Any float uniforms that are left uninitialized will default to 0.0.
