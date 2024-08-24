In the body property, replace the Center widget with a
SingleChildScrollView widget.
Within the SingleChildScrollView widget, replace the Text widget with a
Column widget.
dart diff
- body: const Center(
-   child: Text('Hello World'),
+ body: const SingleChildScrollView(
+   child: Column(
+     children: [
These code updates change the app in the following ways.

A SingleChildScrollView widget can scroll.
  This allows elements that don't fit on the current screen to display.
A Column widget displays any elements within its children property
  in the order listed.
  The first element listed in the children list displays at
  the top of the list. Elements in the children list display
  in array order on the screen from top to bottom.
