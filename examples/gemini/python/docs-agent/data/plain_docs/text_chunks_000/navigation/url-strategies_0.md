Flutter web apps support two ways of configuring
URL-based navigation on the web:
Hash (default)
: Paths are read and written to the hash fragment.
For example, flutterexample.dev/#/path/to/screen.
Path
:  Paths are read and written without a hash. For example,
flutterexample.dev/path/to/screen.
To configure Flutter to use the path instead, use the
usePathUrlStrategy function provided by the flutter_web_plugins library
in the SDK:
```dart
import 'package:flutter_web_plugins/url_strategy.dart';
void main() {
  usePathUrlStrategy();
  runApp(ExampleApp());
}
```
