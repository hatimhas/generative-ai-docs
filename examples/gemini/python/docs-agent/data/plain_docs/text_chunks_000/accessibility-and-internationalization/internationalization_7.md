Dates strings are formatted in many different ways
depending both the locale and the app's needs.  
Placeholder values with type DateTime are formatted with
DateFormat in the intl package.
There are 41 format variations,
identified by the names of their DateFormat factory constructors.
In the following example, the DateTime value
that appears in the helloWorldOn message is
formatted with DateFormat.yMd:
json
"helloWorldOn": "Hello World on ",
"@helloWorldOn": {
  "description": "A message with a date parameter",
  "placeholders": {
    "date": {
      "type": "DateTime",
      "format": "yMd"
    }
  }
}
In an app where the locale is US English,
the following expression would produce  "7/9/1959".
In a Russian locale, it would produce "9.07.1959".
dart
AppLocalizations.of(context).helloWorldOn(DateTime.utc(1959, 7, 9))
