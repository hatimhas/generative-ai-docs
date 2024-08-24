Numbers, including those that represent currency values,
are displayed very differently in different locales. 
The localizations generation tool in
flutter_localizations uses the
NumberFormat
class in the intl package to format
numbers based on the locale and the desired format.
The int, double, and number types can use any of the
following NumberFormat constructors:
| Message "format" value   | Output for 1200000 |
|--------------------------|--------------------|
| compact                | "1.2M"             |
| compactCurrency       | "$1.2M"            |
| compactSimpleCurrency | "$1.2M"            |
| compactLong            | "1.2 million"      |
| currency              | "USD1,200,000.00"  |
| decimalPattern         | "1,200,000"        |
| decimalPatternDigits  | "1,200,000"        |
| decimalPercentPattern | "120,000,000%"     |
| percentPattern         | "120,000,000%"     |
| scientificPattern      | "1E6"              |
| simpleCurrency        | "$1,200,000"       |

The starred NumberFormat constructors in the table
offer optional, named parameters.
Those parameters can be specified as the value
of the placeholder's optionalParameters object.
For example, to specify the optional decimalDigits
parameter for compactCurrency,
make the following changes to the lib/l10n/app_en.arg file:

code-excerpt "gen_l10n_example/lib/l10n/app_en.arb" skip="34" take="13" replace="/},$/}/g"?
json
"numberOfDataPoints": "Number of data points: ",
"@numberOfDataPoints": {
  "description": "A message with a formatted int parameter",
  "placeholders": {
    "value": {
      "type": "int",
      "format": "compactCurrency",
      "optionalParameters": {
        "decimalDigits": 2
      }
    }
  }
}
