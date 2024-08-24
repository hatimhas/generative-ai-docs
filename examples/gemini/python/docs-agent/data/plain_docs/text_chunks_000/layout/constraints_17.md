code-excerpt "lib/main.dart (Example9)" replace="/(return |;)//g"?
dart
ConstrainedBox(
  constraints: const BoxConstraints(
    minWidth: 70,
    minHeight: 70,
    maxWidth: 150,
    maxHeight: 150,
  ),
  child: Container(color: red, width: 10, height: 10),
)
You might guess that the Container has to be
between 70 and 150 pixels, but you would be wrong.
The ConstrainedBox only imposes additional constraints
from those it receives from its parent.
Here, the screen forces the ConstrainedBox to be exactly
the same size as the screen, so it tells its child Container
to also assume the size of the screen, thus ignoring its
constraints parameter.
