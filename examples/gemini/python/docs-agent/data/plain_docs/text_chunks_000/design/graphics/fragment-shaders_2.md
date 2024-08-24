Fragment shaders can be used with most Canvas APIs
by setting Paint.shader.
For example, when using Canvas.drawRect
the shader is evaluated for all fragments within the rectangle.
For an API like Canvas.drawPath with a stroked path,
the shader is evaluated for all fragments within the stroked line.
Some APIs, such as Canvas.drawImage, ignore the value of the shader.
```dart
void paint(Canvas canvas, Size size, FragmentShader shader) {
  // Draws a rectangle with the shader used as a color source.
  canvas.drawRect(
    Rect.fromLTWH(0, 0, size.width, size.height),
    Paint()..shader = shader,
  );
// Draws a stroked rectangle with the shader only applied to the fragments
  // that lie within the stroke.
  canvas.drawRect(
    Rect.fromLTWH(0, 0, size.width, size.height),
    Paint()
      ..style = PaintingStyle.stroke
      ..shader = shader,
  )
}
```
