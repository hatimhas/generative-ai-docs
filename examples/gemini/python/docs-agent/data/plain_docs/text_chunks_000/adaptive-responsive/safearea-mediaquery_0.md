This page discusses how and when to use the
SafeArea and MediaQuery widgets.
When running your app on the latest devices,
you might encounter bits of the UI being blocked
by cutouts on the device's screen.
You can fix this with the SafeArea widget,
which insets its child widget to avoid intrusions
(like notches and camera cutouts),
as well as operating system UI
(such as the status bar on Android),
or by rounded corners of the physical display.
If you don't want this behavior,
the SafeArea widget allows you to
disable padding on any of its four sides.
By default, all four sides are enabled.
It's generally recommended to wrap the body of a
Scaffold widget in SafeArea as a good place to start,
but you don't always need to put it this high in the
Widget tree.
For example, if you purposefully want your app to stretch
under the cutouts, you can move the SafeArea to wrap
whatever content makes sense,
and let the rest of the app take up the full screen.
Using SafeArea ensures that your app content won't be
cut off by physical display features or operating system UI,
and sets your app up for success even as new devices with
different shapes and styles of cutouts enter the market.
How does SafeArea do so much in a small amount of code?
Behind the scenes it uses the MediaQuery object.
