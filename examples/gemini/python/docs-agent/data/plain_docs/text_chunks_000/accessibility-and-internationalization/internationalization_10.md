Some languages with multiple variants require more than just a
language code to properly differentiate.
For example, fully differentiating all variants of
Chinese requires specifying the language code, script code,
and country code. This is due to the existence
of simplified and traditional script, as well as regional
differences in the way characters are written within the same script type.
In order to fully express every variant of Chinese for the
country codes CN, TW, and HK, the list of supported
locales should include:
code-excerpt "gen_l10n_example/lib/examples.dart (supported-locales)"?
dart
supportedLocales: [
  Locale.fromSubtags(languageCode: 'zh'), // generic Chinese 'zh'
  Locale.fromSubtags(
      languageCode: 'zh',
      scriptCode: 'Hans'), // generic simplified Chinese 'zh_Hans'
  Locale.fromSubtags(
      languageCode: 'zh',
      scriptCode: 'Hant'), // generic traditional Chinese 'zh_Hant'
  Locale.fromSubtags(
      languageCode: 'zh',
      scriptCode: 'Hans',
      countryCode: 'CN'), // 'zh_Hans_CN'
  Locale.fromSubtags(
      languageCode: 'zh',
      scriptCode: 'Hant',
      countryCode: 'TW'), // 'zh_Hant_TW'
  Locale.fromSubtags(
      languageCode: 'zh',
      scriptCode: 'Hant',
      countryCode: 'HK'), // 'zh_Hant_HK'
],
This explicit full definition ensures that your app can
distinguish between and provide the fully nuanced localized
content to all combinations of these country codes.
If a user's preferred locale isn't specified,
Flutter selects the closest match,
which likely contains differences to what the user expects.
Flutter only resolves to locales defined in supportedLocales
and provides scriptCode-differentiated localized
content for commonly used languages.
See Localizations for information on how the supported
locales and the preferred locales are resolved.
Although Chinese is a primary example,
other languages like French (fr_FR, fr_CA)
should also be fully differentiated for more nuanced localization.
