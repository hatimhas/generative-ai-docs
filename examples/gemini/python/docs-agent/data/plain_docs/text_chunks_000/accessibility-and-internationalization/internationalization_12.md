Although the flutter_localizations library currently supports
} languages and language variants, only English language translations
are available by default. It's up to the developer to decide exactly
which languages to support.
The MaterialApp supportedLocales
parameter limits locale changes. When the user changes the locale
setting on their device, the app's Localizations widget only
follows suit if the new locale is a member of this list.
If an exact match for the device locale isn't found,
then the first supported locale with a matching languageCode
is used. If that fails, then the first element of the
supportedLocales list is used.
An app that wants to use a different "locale resolution"
method can provide a localeResolutionCallback.
For example, to have your app unconditionally accept
whatever locale the user selects:
code-excerpt "gen_l10n_example/lib/examples.dart (locale-resolution)"?
dart
MaterialApp(
  localeResolutionCallback: (
    locale,
    supportedLocales,
  ) {
    return locale;
  },
);
