Localizations.override is a factory constructor
for the Localizations widget that allows for
(the typically rare) situation where a section of your application
needs to be localized to a different locale than the locale
configured for your device. 
To observe this behavior, add a call to Localizations.override
and a simple CalendarDatePicker:
code-excerpt "gen_l10n_example/lib/examples.dart (date-picker)"?
dart
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(
      title: Text(widget.title),
    ),
    body: Center(
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: <Widget>[
          // Add the following code
          Localizations.override(
            context: context,
            locale: const Locale('es'),
            // Using a Builder to get the correct BuildContext.
            // Alternatively, you can create a new widget and Localizations.override
            // will pass the updated BuildContext to the new widget.
            child: Builder(
              builder: (context) {
                // A toy example for an internationalized Material widget.
                return CalendarDatePicker(
                  initialDate: DateTime.now(),
                  firstDate: DateTime(1900),
                  lastDate: DateTime(2100),
                  onDateChanged: (value) {},
                );
              },
            ),
          ),
        ],
      ),
    ),
  );
}
Hot reload the app and the CalendarDatePicker
widget should re-render in Spanish.
