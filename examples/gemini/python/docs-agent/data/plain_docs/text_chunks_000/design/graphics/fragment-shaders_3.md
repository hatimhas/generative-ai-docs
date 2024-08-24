Fragment shaders are authored as GLSL source files.
By convention, these files have the .frag extension.
(Flutter doesn't support vertex shaders,
which would have the .vert extension.)
Any GLSL version from 460 down to 100 is supported,
though some available features are restricted.
The rest of the examples in this document use version 460 core.
Shaders are subject to the following limitations
when used with Flutter:

UBOs and SSBOs aren't supported
sampler2D is the only supported sampler type
Only the two-argument version of texture (sampler and uv) is supported
No additional varying inputs can be declared
All precision hints are ignored when targeting Skia
Unsigned integers and booleans aren't supported
