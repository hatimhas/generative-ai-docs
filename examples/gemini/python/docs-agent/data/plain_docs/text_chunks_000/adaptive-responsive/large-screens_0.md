code-excerpt path-base="ui/adaptive_app_demos"?
This page provides guidance on optimizing your
app to improve its behavior on large screens.
Flutter, like Android, defines large screens as tablets,
foldables, and ChromeOS devices running Android. Flutter
also defines large screen devices as web, desktop,
and iPads.
:::secondary Why do large screens matter, in particular?
Demand for large screens continues to increase.
As of January 2024,
more than 270 million active large screen
and foldable devices run on Android and more than
14.9 million iPad users.
When your app supports large screens,
it also receives other benefits.
Optimizing your app to fill the screen.
For example, it:

Improves your app's user engagement metrics.
Increases your app's visibility in the Play Store.
  Recent Play Store updates show ratings by
  device type and indicates when an app lacks
  large screen support. 
Ensures that your app meets iPadOS submission
  guidelines and is accepted in the App Store.
:::

Consider the following screenshots of an app.
The app displays its UI in a ListView.
The image on the left shows the app running
on a mobile device. The image on the right shows the
app running on a large screen device
before the advice on this page was applied.

This is not optimal.
The Android Large Screen App Quality Guidelines
and the iOS equivalent
say that neither text nor boxes should take up the
full screen width. How to solve this in an adaptive way?
A common solution uses GridView, as shown in the next section.
