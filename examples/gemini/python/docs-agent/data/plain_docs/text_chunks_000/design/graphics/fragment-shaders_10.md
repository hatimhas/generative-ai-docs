When targeting the Skia backend,
loading the shader might be expensive since it
must be compiled to the appropriate
platform-specific shader at runtime.
If you intend to use one or more shaders during an animation,
consider precaching the fragment program objects before
starting the animation.
You can reuse a FragmentShader object across frames;
this is more efficient than creating a new
FragmentShader for each frame.
For a more detailed guide on writing performant shaders,
check out Writing efficient shaders on GitHub.
