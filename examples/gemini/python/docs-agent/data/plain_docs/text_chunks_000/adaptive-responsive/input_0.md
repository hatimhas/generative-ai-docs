code-excerpt path-base="ui/adaptive_app_demos"?
It isn't enough to just adapt how your app looks,
you also have to support a variety of user inputs.
The mouse and keyboard introduce input types beyond those
found on a touch device, like scroll wheel, right-click,
hover interactions, tab traversal, and keyboard shortcuts.
Some of these features work by default on Material
widgets. But, if you've created a custom widget,
you might need to implement them directly.
Some features that encompass a well-designed app,
also help users who work with assistive technologies.
For example, aside from being good app design,
some features, like tab traversal and keyboard shortcuts,
are critical for users who work with assistive devices.
In addition to the standard advice for
creating accessible apps, this page covers
info for creating apps that are both
adaptive and accessible.
Scrolling widgets like ScrollView or ListView
support the scroll wheel by default, and because
almost every scrollable custom widget is built
using one of these, it works with those as well.
If you need to implement custom scroll behavior,
you can use the Listener widget, which lets you
customize how your UI reacts to the scroll wheel.
code-excerpt "lib/widgets/extra_widget_excerpts.dart (pointer-scroll)"?
dart
return Listener(
  onPointerSignal: (event) {
    if (event is PointerScrollEvent) print(event.scrollDelta.dy);
  },
  child: ListView(),
);
