The shader has access to a varying value that contains the local coordinates for
the particular fragment being evaluated. Use this feature to compute
effects that depend on the current position, which can be accessed by
importing the flutter/runtime_effect.glsl library and calling the
FlutterFragCoord function. For example:
```glsl
