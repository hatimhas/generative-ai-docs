These values need to be modified for the locale to use the correct
date formatting. Unfortunately, since the intl library doesn't
share the same flexibility for number formatting,
the formatting for an existing locale must be used
as a substitute in _NnMaterialLocalizationsDelegate:
code-excerpt "add_language/lib/nn_intl.dart (delegate)"?
``dart
class _NnMaterialLocalizationsDelegate
    extends LocalizationsDelegate {
  const _NnMaterialLocalizationsDelegate();
@override
  bool isSupported(Locale locale) => locale.languageCode == 'nn';
@override
  Future load(Locale locale) async {
    final String localeName = intl.Intl.canonicalizedLocale(locale.toString());
// The locale (in this casenn`) needs to be initialized into the custom
// date symbols and patterns setup that Flutter uses.
date_symbol_data_custom.initializeDateFormattingCustom(
  locale: localeName,
  patterns: nnLocaleDatePatterns,
  symbols: intl.DateSymbols.deserializeFromMap(nnDateSymbols),
);
return SynchronousFuture(
  NnMaterialLocalizations(
    localeName: localeName,
    // The intl library's NumberFormat class is generated from CLDR data
    // (see https://github.com/dart-lang/i18n/blob/main/pkgs/intl/lib/number_symbols_data.dart).
    // Unfortunately, there is no way to use a locale that isn't defined in
    // this map and the only way to work around this is to use a listed
    // locale's NumberFormat symbols. So, here we use the number formats
    // for 'en_US' instead.
    decimalFormat: intl.NumberFormat('#,##0.###', 'en_US'),
    twoDigitZeroPaddedFormat: intl.NumberFormat('00', 'en_US'),
    // DateFormat here will use the symbols and patterns provided in the
    // date_symbol_data_custom.initializeDateFormattingCustom call above.
    // However, an alternative is to simply use a supported locale's
    // DateFormat symbols, similar to NumberFormat above.
    fullYearFormat: intl.DateFormat('y', localeName),
    compactDateFormat: intl.DateFormat('yMd', localeName),
    shortDateFormat: intl.DateFormat('yMMMd', localeName),
    mediumDateFormat: intl.DateFormat('EEE, MMM d', localeName),
    longDateFormat: intl.DateFormat('EEEE, MMMM d, y', localeName),
    yearMonthFormat: intl.DateFormat('MMMM y', localeName),
    shortMonthDayFormat: intl.DateFormat('MMM d'),
  ),
);
}
@override
  bool shouldReload(_NnMaterialLocalizationsDelegate old) => false;
}
```
For more information about localization strings,
check out the flutter_localizations README.
Once you've implemented your language-specific subclasses of
GlobalMaterialLocalizations and LocalizationsDelegate,
you  need to add the language and a delegate instance to your app.
The following code sets the app's language to Nynorsk and
adds the NnMaterialLocalizations delegate instance to the app's
localizationsDelegates list:
code-excerpt "add_language/lib/main.dart (material-app)"?
dart
const MaterialApp(
  localizationsDelegates: [
    GlobalWidgetsLocalizations.delegate,
    GlobalMaterialLocalizations.delegate,
    NnMaterialLocalizations.delegate, // Add the newly created delegate
  ],
  supportedLocales: [
    Locale('en', 'US'),
    Locale('nn'),
  ],
  home: Home(),
),
