You can debug accessibility by visualizing the semantic nodes created for your web app
using the following command line flag in profile and release modes:
console
flutter run -d chrome --profile --dart-define=FLUTTER_WEB_DEBUG_SHOW_SEMANTICS=true
With the flag activated, the semantic nodes appear on top of the widgets;
you can verify that the semantic elements are placed where they should be.
If the semantic nodes are incorrectly placed, please file a bug report.
