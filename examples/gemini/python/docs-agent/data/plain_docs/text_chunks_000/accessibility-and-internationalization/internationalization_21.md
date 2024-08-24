The previous example was defined in terms of the Dart intl
package. You can choose your own approach for managing
localized values for the sake of simplicity or perhaps to integrate
with a different i18n framework.
Complete source code for the minimal app.
In the following example, the DemoLocalizations class 
includes all of its translations directly in per language Maps:
code-excerpt "minimal/lib/main.dart (demo)"?
```dart
class DemoLocalizations {
  DemoLocalizations(this.locale);
final Locale locale;
static DemoLocalizations of(BuildContext context) {
    return Localizations.of(context, DemoLocalizations)!;
  }
static const _localizedValues = >{
    'en': {
      'title': 'Hello World',
    },
    'es': {
      'title': 'Hola Mundo',
    },
  };
static List languages() => _localizedValues.keys.toList();
String get title {
    return _localizedValues[locale.languageCode]!['title']!;
  }
}
```
In the minimal app the DemoLocalizationsDelegate is slightly
different. Its load method returns a SynchronousFuture
because no asynchronous loading needs to take place.
code-excerpt "minimal/lib/main.dart (delegate)"?
```dart
class DemoLocalizationsDelegate
    extends LocalizationsDelegate {
  const DemoLocalizationsDelegate();
@override
  bool isSupported(Locale locale) =>
      DemoLocalizations.languages().contains(locale.languageCode);
@override
  Future load(Locale locale) {
    // Returning a SynchronousFuture here because an async "load" operation
    // isn't needed to produce an instance of DemoLocalizations.
    return SynchronousFuture(DemoLocalizations(locale));
  }
@override
  bool shouldReload(DemoLocalizationsDelegate old) => false;
}
```
