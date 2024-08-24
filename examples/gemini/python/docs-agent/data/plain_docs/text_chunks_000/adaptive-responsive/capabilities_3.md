The simplest mechanical way is Platform.isAndroid,
Platform.isIOS, and kIsWeb. These APIs mechanically
let you know where the code is running but have some
problems as the app expands where it can run, and
as host platforms add functionality. 
The following guidelines explain best practices
when developing the capabilities and policies for your app:
Avoid using Platform.isAndroid and similar functions
to make layout decisions or assumptions about what a device can do.
Instead, describe what you want to branch on in a method. 
Example: Your app has a link to buy something in a
website, but you don't want to show that link on iOS
devices for policy reasons. 
```dart
bool shouldAllowPurchaseClick() {
  // Banned by Apple App Store guidelines. 
  return !Platform.isIOS;
}
...
TextSpan(
  text: 'Buy in browser',
  style: new TextStyle(color: Colors.blue),
  recognizer: shouldAllowPurchaseClick ? TapGestureRecognizer()
    ..onTap = () { launch('') : null;
  } : null,
```
What did you get by adding an additional layer of indirection?
The code makes it more clear why the branched path exists.
This method can exist directly in the class but it's likely
that other parts of the code might need this same check.
If so, put the code in a class. 
```dart title="policy.dart"
class Policy {
bool shouldAllowPurchaseClick() {
    // Banned by Apple App Store guidelines. 
    return !Platform.isIOS;
  }
}
```
With this code in a class, any widget test can mock
Policy().shouldAllowPurchaseClick and verify the behavior
independently of where the device runs. 
It also means that later, if you decide that
buying on the web isn't the right flow for
Android users, you can change the implementation
and the tests for clickable text won't need to change.
