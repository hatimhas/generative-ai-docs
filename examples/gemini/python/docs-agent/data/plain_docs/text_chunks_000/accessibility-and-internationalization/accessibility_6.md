Test your app using Flutter's Accessibility Guideline API.
This API checks if your app's UI meets Flutter's accessibility recommendations.
These cover recommendations for text contrast, target size, and target labels.
The following example shows how to use the Guideline API on Name Generator.
You created this app as part of the
Write your first Flutter app codelab.
Each button on the app's main screen serves as a tappable target
with text represented in 18 point.
code-excerpt path-base="codelabs/namer/step_08"?
code-excerpt "test/a11y_test.dart (insideTest)"?
```dart
final SemanticsHandle handle = tester.ensureSemantics();
await tester.pumpWidget(MyApp());
// Checks that tappable nodes have a minimum size of 48 by 48 pixels
// for Android.
await expectLater(tester, meetsGuideline(androidTapTargetGuideline));
// Checks that tappable nodes have a minimum size of 44 by 44 pixels
// for iOS.
await expectLater(tester, meetsGuideline(iOSTapTargetGuideline));
// Checks that touch targets with a tap or long press action are labeled.
await expectLater(tester, meetsGuideline(labeledTapTargetGuideline));
// Checks whether semantic nodes meet the minimum text contrast levels.
// The recommended text contrast is 3:1 for larger text
// (18 point and above regular).
await expectLater(tester, meetsGuideline(textContrastGuideline));
handle.dispose();
```
You can add Guideline API tests
in test/widget_test.dart of your app directory, or as a separate test
file (such as test/a11y_test.dart in the case of the Name Generator).
