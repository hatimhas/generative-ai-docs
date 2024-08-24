:::tip
When using VS Code, add the arb-editor extension.
This extension adds syntax highlighting, snippets, 
diagnostics, and quick fixes to help edit .arb template files.
:::
You can also include application values in a message with
special syntax that uses a placeholder to generate a method
instead of a getter.
A placeholder, which must be a valid Dart identifier name,
becomes a positional parameter in the generated method in the
AppLocalizations code. Define a placeholder name by wrapping
it in curly braces as follows:
json
""
Define each placeholder in the placeholders object
in the app's .arb file. For example,
to define a hello message with a userName parameter,
add the following to lib/l10n/app_en.arb:
code-excerpt "gen_l10n_example/lib/l10n/app_en.arb" skip="5" take="10" replace="/},$/}/g"?
json
"hello": "Hello ",
"@hello": {
  "description": "A message with a single parameter",
  "placeholders": {
    "userName": {
      "type": "String",
      "example": "Bob"
    }
  }
}
This code snippet adds a hello method call to
the AppLocalizations.of(context) object,
and the method accepts a parameter of type String;
the hello method returns a string.
Regenerate the AppLocalizations file.
Replace the code passed into Builder with the following:
code-excerpt "gen_l10n_example/lib/main.dart (placeholder)" remove="/wombat|Wombats|he'|they|pronoun/"?
dart
// Examples of internationalized strings.
return Column(
  children: <Widget>[
    // Returns 'Hello John'
    Text(AppLocalizations.of(context)!.hello('John')),
  ],
);
You can also use numerical placeholders to specify multiple values.
Different languages have different ways to pluralize words.
The syntax also supports specifying how a word should be pluralized.
A pluralized message must include a num parameter indicating
how to pluralize the word in different situations.
English, for example, pluralizes "person" to "people",
but that doesn't go far enough.
The message0 plural might be "no people" or "zero people".
The messageFew plural might be
"several people", "some people", or "a few people". 
The messageMany plural might
be  "most people" or "many people", or "a crowd". 
Only the more general messageOther field is required.
The following example shows what options are available:
json
" =1 =2 few many other}"
The previous expression is replaced by the message variation
(message0, message1, ...) corresponding to the value
of the countPlaceholder.
Only the messageOther field is required.
The following example defines a message that pluralizes
the word, "wombat":

code-excerpt "gen_l10n_example/lib/l10n/app_en.arb" skip="15" take="10" replace="/},$/}/g"?
json
"nWombats": " =1 other wombats}}",
"@nWombats": {
  "description": "A plural message",
  "placeholders": {
    "count": {
      "type": "num",
      "format": "compact"
    }
  }
}

Use a plural method by passing in the count parameter:
code-excerpt "gen_l10n_example/lib/main.dart (placeholder)" remove="/John|he|she|they|pronoun/" replace="/\[/[\n    .../g"?
dart
// Examples of internationalized strings.
return Column(
  children: <Widget>[
    ...
    // Returns 'no wombats'
    Text(AppLocalizations.of(context)!.nWombats(0)),
    // Returns '1 wombat'
    Text(AppLocalizations.of(context)!.nWombats(1)),
    // Returns '5 wombats'
    Text(AppLocalizations.of(context)!.nWombats(5)),
  ],
);
Similar to plurals,
you can also choose a value based on a String placeholder.
This is most often used to support gendered languages.
The syntax is as follows:
json
" ... other}"
The next example defines a message that
selects a pronoun based on gender:

code-excerpt "gen_l10n_example/lib/l10n/app_en.arb" skip="25" take="9" replace="/},$/}/g"?
json
"pronoun": " female other}",
"@pronoun": {
  "description": "A gendered message",
  "placeholders": {
    "gender": {
      "type": "String"
    }
  }
}

Use this feature by
passing the gender string as a parameter:
code-excerpt "gen_l10n_example/lib/main.dart (placeholder)" remove="/'He|hello|ombat/" replace="/\[/[\n    .../g"?
dart
// Examples of internationalized strings.
return Column(
  children: <Widget>[
    ...
    // Returns 'he'
    Text(AppLocalizations.of(context)!.pronoun('male')),
    // Returns 'she'
    Text(AppLocalizations.of(context)!.pronoun('female')),
    // Returns 'they'
    Text(AppLocalizations.of(context)!.pronoun('other')),
  ],
);
Keep in mind that when using select statements,
comparison between the parameter and the actual
value is case-sensitive.
That is, AppLocalizations.of(context)!.pronoun("Male")
defaults to the "other" case, and returns "they".
