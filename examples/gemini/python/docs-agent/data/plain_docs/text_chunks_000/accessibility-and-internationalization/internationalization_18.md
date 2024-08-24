An app that needs to support a language that's not included in
GlobalMaterialLocalizations has to do some extra work:
it must provide about 70 translations ("localizations")
for words or phrases and the date patterns and symbols for the
locale.
See the following for an example of how to add
support for the Norwegian Nynorsk language.
A new GlobalMaterialLocalizations subclass defines the
localizations that the Material library depends on.
A new LocalizationsDelegate subclass, which serves
as factory for the GlobalMaterialLocalizations subclass,
must also be defined.
Here's the source code for the complete add_language example,
minus the actual Nynorsk translations.
The locale-specific GlobalMaterialLocalizations subclass
is called NnMaterialLocalizations,
and the LocalizationsDelegate subclass is
_NnMaterialLocalizationsDelegate.
The value of NnMaterialLocalizations.delegate
is an instance of the delegate, and is all
that's needed by an app that uses these localizations.
The delegate class includes basic date and number format
localizations. All of the other localizations are defined by String
valued property getters in NnMaterialLocalizations, like this:
code-excerpt "add_language/lib/nn_intl.dart (getters)"?
dart
@override
String get moreButtonTooltip => r'More';
@override
String get aboutListTileTitleRaw => r'About $applicationName';
@override
String get alertDialogLabel => r'Alert';
These are the English translations, of course.
To complete the job you need to change the return
value of each getter to an appropriate Nynorsk string.
The getters return "raw" Dart strings that have an r prefix,
such as r'About $applicationName',
because sometimes the strings contain variables with a $ prefix.
The variables are expanded by parameterized localization methods:
code-excerpt "add_language/lib/nn_intl.dart (raw)"?
dart
@override
String get pageRowsInfoTitleRaw => r'$firstRow–$lastRow of $rowCount';
@override
String get pageRowsInfoTitleApproximateRaw =>
    r'$firstRow–$lastRow of about $rowCount';
The date patterns and symbols of the locale also need to
be specified, which are defined in the source code as follows:
RegEx adds last two lines with commented out code and closing bracket.
code-excerpt "add_language/lib/nn_intl.dart (date-patterns)" replace="/  'LLL': 'LLL',/  'LLL': 'LLL',\n  \/\/ ...\n}/g"?
dart
const nnLocaleDatePatterns = {
  'd': 'd.',
  'E': 'ccc',
  'EEEE': 'cccc',
  'LLL': 'LLL',
  // ...
}
RegEx adds last two lines with commented out code and closing bracket.
code-excerpt "add_language/lib/nn_intl.dart (date-symbols)" replace="/  ],/  ],\n  \/\/ ...\n}/g"?
dart
const nnDateSymbols = {
  'NAME': 'nn',
  'ERAS': [
    'f.Kr.',
    'e.Kr.',
  ],
  // ...
}
