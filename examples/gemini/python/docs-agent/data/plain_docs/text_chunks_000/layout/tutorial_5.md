Add the TitleSection widget as the first element in the children list.
This places it at the top of the screen.
Pass the provided name and location to the TitleSection constructor.
dart diff
+ children: [
+   TitleSection(
+     name: 'Oeschinen Lake Campground',
+     location: 'Kandersteg, Switzerland',
+   ),
+ ],
:::tip
* When pasting code into your app, indentation can become skewed.
  To fix this in your Flutter editor, use automatic reformatting support.
* To accelerate your development, try Flutter's hot reload feature.
* If you have problems, compare your code to lib/main.dart.
:::
