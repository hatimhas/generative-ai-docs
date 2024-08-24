code-excerpt path-base="internationalization"?

Consider updating the number of languages when touching this page.


:::secondary What you'll learn
* How to track the device's locale (the user's preferred language).
* How to enable locale-specific Material or Cupertino widgets.
* How to manage locale-specific app values.
* How to define the locales an app supports.
:::
If your app might be deployed to users who speak another
language then you'll need to internationalize it.
That means you need to write the app in a way that makes
it possible to localize values like text and layouts
for each language or locale that the app supports.
Flutter provides widgets and classes that help with
internationalization and the Flutter libraries
themselves are internationalized.
This page covers concepts and workflows necessary to
localize a Flutter application using the
MaterialApp and CupertinoApp classes,
as most apps are written that way.
However, applications written using the lower level
WidgetsApp class can also be internationalized
using the same classes and logic.
This section provides a tutorial on how to create and
internationalize a new Flutter application,
along with any additional setup
that a target platform might require.
You can find the source code for this example in
gen_l10n_example.
