As mentioned previously, Android and Flutter both
recommend in their design guidance not
to lock screen orientation,
but some apps lock screen orientation anyway.
Be aware that this can cause problems when running your
app on a foldable device.
When running on a foldable, the app might look ok
when the device is folded. But when unfolding,
you might find the app letterboxed.
As described in the SafeArea & MediaQuery page,
letterboxing means that the app's window is locked to
the center of the screen while the window is
surrounded with black.
Why can this happen?
This can happen when using MediaQuery to figure out
the window size for your app. When the device is folded,
orientation is restricted to portrait mode.
Under the hood, setPreferredOrientations causes
Android to use a portrait compatibility mode and the app
is displayed in a letterboxed state.
In the letterboxed state, MediaQuery never receives
the larger window size that allows the UI to expand.
You can solve this in one of two ways:

Support all orientations.
Use the dimensions of the physical display.
  In fact, this is one of the few situations where
  you would use the physical display dimensions and
  not the window dimensions.

How to obtain the physical screen dimensions?
You can use the Display API, introduced in
Flutter 3.13, which contains the size,
pixel ratio, and the refresh rate of the physical device. 
The following sample code retrieves a Display object:
```dart
/// AppState object.
ui.FlutterView? _view;
@override
void didChangeDependencies() {
  super.didChangeDependencies();
  _view = View.maybeOf(context);
}
void didChangeMetrics() {
  final ui.Display? display = _view?.display;
}
```
The important thing is to find the display of the
view that you care about. This creates a forward-looking
API that should handle current and future multi-display
and multi-view devices.
