In the past, you might have used MediaQuery.of to
determine the size of the device's screen.
However, devices today feature screens
with a wide variety of sizes and shapes,
and this test can be misleading.
For example, maybe your app currently occupies a
small window on a large screen. If you use the
MediaQuery.of method and conclude the screen to be small
(when, in fact, the app displays in a tiny window on a large screen),
and you've portrait locked your app, it causes the
app's window to lock to the center of the
screen, surrounded with black.
This is hardly an ideal UI on a large screen.
:::note
The Material Guidelines encourage you to never
portrait lock your app (by disabling landscape mode).
However, if you feel you really must,
then at least define the portrait mode to work
in top-down mode as well as bottom up.
:::
Keep in mind that MediaQuery.sizeOf returns the
current size of the app's entire screen and
not just a single widget.
You have two ways to measure your screen space.
You can use either MediaQuery.sizeOf or LayoutBuilder,
depending on whether you want the size of the whole
app window, or more local sizing.
If you want your widget to be fullscreen,
even when the app window is small,
use MediaQuery.sizeOf so you can choose the
UI based on the size of the app window itself.
In the previous section, you want to base the
sizing behavior on the entire app's window,
so you would use MediaQuery.sizeOf.
:::secondary Why use MediaQuery.sizeOf instead of MediaQuery.of?
Previous advice recommended that you use the of method of
MediaQuery to obtain the app window's dimensions.
Why has this advice changed?
The short answer is for performance reasons. 
MediaQuery contains a lot of data, but if you're
only interested in the size property, it's more
efficient to use the sizeOf method. Both methods
return the size of the app window in logical pixels
(also known as density independent pixels).
The logical pixel dimensions generally works best as its
roughly the same visual size across all devices.
The MediaQuery class has other specialized functions
for each of its individual properties for the same reason.
:::
Requesting the size of the app window from inside
the build method, as in MediaQuery.sizeOf(context),
causes the given BuildContext to rebuild any time
the size property changes.
