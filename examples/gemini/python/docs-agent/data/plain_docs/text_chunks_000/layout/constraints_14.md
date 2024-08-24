code-excerpt "lib/main.dart (Example6)" replace="/(return |;)//g"?
dart
Center(
  child: Container(color: red),
)
The screen forces the Center to be exactly the
same size as the screen, so the Center fills the screen.
The Center tells the Container that it can be any
size it wants, but not bigger than the screen.
Since the Container has no child and no fixed size,
it decides it wants to be as big as possible,
so it fills the whole screen.
But why does the Container decide that?
Simply because that's a design decision by those who
created the Container widget. It could have been
created differently, and you have to read the
Container API documentation to understand
how it behaves, depending on the circumstances.
