The l10n.yaml file allows you to configure the gen-l10n tool
to specify the following:
where all the input files are located
where all the output files should be created
what Dart class name to give your localizations delegate
For a full list of options, either run flutter gen-l10n --help
at the command line or refer to the following table:
| Option                              | Description |
| ------------------------------------| ------------------ |
| arb-dir                           | The directory where the template and translated arb files are located. The default is lib/l10n. |
| output-dir                        | The directory where the generated localization classes are written. This option is only relevant if you want to generate the localizations code somewhere else in the Flutter project. You also need to set the synthetic-package flag to false.The app must import the file specified in the output-localization-file option from this directory. If unspecified, this defaults to the same directory as the input directory specified in arb-dir. |
| template-arb-file                 | The template arb file that is used as the basis for generating the Dart localization and messages files. The default is app_en.arb. |
| output-localization-file          | The filename for the output localization and localizations delegate classes. The default is app_localizations.dart. |
| untranslated-messages-file        | The location of a file that describes the localization messages haven't been translated yet. Using this option creates a JSON file at the target location, in the following format:  "locale": ["message_1", "message_2" ... "message_n"] If this option is not specified, a summary of the messages that haven't been translated are printed on the command line. |
