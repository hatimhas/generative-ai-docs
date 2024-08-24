Sometimes, you have to use tokens,
such as , as normal characters.
To ignore such tokens from being parsed,
enable the use-escaping flag by adding the
following to l10n.yaml:
yaml
use-escaping: true
The parser ignores any string of characters
wrapped with a pair of single quotes.
To use a normal single quote character,
use a pair of consecutive single quotes.
For example, the follow text is converted
to a Dart String:
json
{
  "helloWorld": "Hello! '' this a wonderful day?"
}
The resulting string is as follows:
dart
"Hello!  this a wonderful day?"
