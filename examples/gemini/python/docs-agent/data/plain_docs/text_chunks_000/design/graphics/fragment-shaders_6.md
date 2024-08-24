void main() {
  vec2 currentPos = FlutterFragCoord().xy;
}
```
The value returned from FlutterFragCoord is distinct from gl_FragCoord.
gl_FragCoord provides the screen space coordinates and should generally be
avoided to ensure that shaders are consistent across backends.
When targeting a Skia backend,
the calls to gl_FragCoord are rewritten to access local
coordinates but this rewriting isn't possible with Impeller.
