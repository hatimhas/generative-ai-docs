The Localizations widget is used to load and
look up objects that contain collections of localized values.
Apps refer to these objects with Localizations.of(context,type).
If the device's locale changes,
the Localizations widget automatically loads values for
the new locale and then rebuilds widgets that used it.
This happens because Localizations works like an
InheritedWidget.
When a build function refers to an inherited widget,
an implicit dependency on the inherited widget is created.
When an inherited widget changes
(when the Localizations widget's locale changes),
its dependent contexts are rebuilt.
Localized values are loaded by the Localizations widget's
list of LocalizationsDelegates.
Each delegate must define an asynchronous load()
method that produces an object that encapsulates a
collection of localized values.
Typically these objects define one method per localized value.
In a large app, different modules or packages might be bundled with
their own localizations. That's why the Localizations widget
manages a table of objects, one per LocalizationsDelegate.
To retrieve the object produced by one of the LocalizationsDelegate's
load methods, specify a BuildContext and the object's type.
For example,
the localized strings for the Material Components widgets
are defined by the MaterialLocalizations class.
Instances of this class are created by a LocalizationDelegate
provided by the MaterialApp class.
They can be retrieved with Localizations.of():
dart
Localizations.of<MaterialLocalizations>(context, MaterialLocalizations);
This particular Localizations.of() expression is used frequently,
so the MaterialLocalizations class provides a convenient shorthand:
```dart
static MaterialLocalizations of(BuildContext context) {
  return Localizations.of(context, MaterialLocalizations);
}
/// References to the localized values defined by MaterialLocalizations
/// are typically written like this:
tooltip: MaterialLocalizations.of(context).backButtonTooltip,
```
