The FavoriteWidget class manages its own state,
so it overrides createState() to create a State
object. The framework calls createState()
when it wants to build the widget.
In this example, createState() returns an
instance of _FavoriteWidgetState,
which you'll implement in the next step.
code-excerpt path-base="layout/lakes/interactive"?
code-excerpt "lib/main.dart (favorite-widget)"?
```dart
class FavoriteWidget extends StatefulWidget {
  const FavoriteWidget();
@override
  State createState() => _FavoriteWidgetState();
}
```
:::note
Members or classes that start with an underscore
(_) are private. For more information,
see Libraries and imports, a section in the
Dart language documentation.
:::
