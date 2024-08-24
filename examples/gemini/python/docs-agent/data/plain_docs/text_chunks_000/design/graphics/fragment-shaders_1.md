To load a shader into a FragmentProgram object at runtime,
use the FragmentProgram.fromAsset constructor.
The asset's name is the same as the path to the shader
given in the pubspec.yaml file.
dart
void loadMyShader() async {
  var program = await FragmentProgram.fromAsset('shaders/myshader.frag');
}
The FragmentProgram object can be used to create
one or more FragmentShader instances.
A FragmentShader object represents a fragment program
along with a particular set of uniforms (configuration parameters).
The available uniforms depends on how the shader was defined.
dart
void updateShader(Canvas canvas, Rect rect, FragmentProgram program) {
  var shader = program.fragmentShader();
  shader.setFloat(0, 42.0);
  canvas.drawRect(rect, Paint()..shader = shader);
}
