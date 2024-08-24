The Locale class identifies the user's language.
Mobile devices support setting the locale for all applications,
usually using a system settings menu.
Internationalized apps respond by displaying values that are
locale-specific. For example, if the user switches the device's locale
from English to French, then a Text widget that originally
displayed "Hello World" would be rebuilt with "Bonjour le monde".
The Localizations widget defines the locale
for its child and the localized resources that the child depends on.
The WidgetsApp widget creates a Localizations widget
and rebuilds it if the system's locale changes.
You can always look up an app's current locale with
Localizations.localeOf():
code-excerpt "gen_l10n_example/lib/examples.dart (my-locale)"?
dart
Locale myLocale = Localizations.localeOf(context);
