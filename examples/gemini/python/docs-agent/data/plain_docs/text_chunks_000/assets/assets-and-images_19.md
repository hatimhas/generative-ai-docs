Flutter also uses native platform mechanisms to draw
transitional launch screens to your Flutter app while the
Flutter framework loads. This launch screen persists until
Flutter renders the first frame of your application.
:::note
This implies that if you don't call runApp() in the
main() function of your app (or more specifically,
if you don't call FlutterView.render() in response to
PlatformDispatcher.onDrawFrame),
the launch screen persists forever.
:::
