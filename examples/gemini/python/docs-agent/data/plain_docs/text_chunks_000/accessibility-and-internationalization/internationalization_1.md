By default, Flutter only provides US English localizations.
To add support for other languages,
an application must specify additional
MaterialApp (or CupertinoApp) properties,
and include a package called flutter_localizations.
As of December 2023, this package supports } languages
and language variants.
To begin, start by creating a new Flutter application
in a directory of your choice with the flutter create command.
console
$ flutter create <name_of_flutter_app>
To use flutter_localizations,
add the package as a dependency to your pubspec.yaml file, 
as well as the intl package:
console
$ flutter pub add flutter_localizations --sdk=flutter
$ flutter pub add intl:any
This creates a pubspec.yml file with the following entries:
code-excerpt "gen_l10n_example/pubspec.yaml (flutter-localizations)"?
yaml
dependencies:
  flutter:
    sdk: flutter
  flutter_localizations:
    sdk: flutter
  intl: any
Then import the flutter_localizations library and specify
localizationsDelegates and supportedLocales for
your MaterialApp or CupertinoApp:
code-excerpt "gen_l10n_example/lib/main.dart (localization-delegates-import)"?
dart
import 'package:flutter_localizations/flutter_localizations.dart';
code-excerpt "gen_l10n_example/lib/main.dart (material-app)" remove="AppLocalizations.delegate"?
dart
return const MaterialApp(
  title: 'Localizations Sample App',
  localizationsDelegates: [
    GlobalMaterialLocalizations.delegate,
    GlobalWidgetsLocalizations.delegate,
    GlobalCupertinoLocalizations.delegate,
  ],
  supportedLocales: [
    Locale('en'), // English
    Locale('es'), // Spanish
  ],
  home: MyHomePage(),
);
After introducing the flutter_localizations package
and adding the previous code,
the Material and Cupertino
packages should now be correctly localized in
one of the } supported locales.
Widgets should be adapted to the localized messages,
along with correct left-to-right or right-to-left layout.
Try switching the target platform's locale to
Spanish (es) and the messages should be localized.
Apps based on WidgetsApp are similar except that the
GlobalMaterialLocalizations.delegate isn't needed.
The full Locale.fromSubtags constructor is preferred
as it supports scriptCode, though the Locale default
constructor is still fully valid.
The elements of the localizationsDelegates list are
factories that produce collections of localized values.
GlobalMaterialLocalizations.delegate provides localized
strings and other values for the Material Components
library. GlobalWidgetsLocalizations.delegate
defines the default text direction,
either left-to-right or right-to-left, for the widgets library.
More information about these app properties, the types they
depend on, and how internationalized Flutter apps are typically
structured, is covered in this page.
