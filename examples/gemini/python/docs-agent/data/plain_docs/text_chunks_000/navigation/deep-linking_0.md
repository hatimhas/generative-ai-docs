Deep links are links that not only open an app, but also take the
user to a specific location "deep" inside the app. For example,
a deep link from an advertisement for a pair of sneakers might open
a shopping app and display the product page for those particular shoes.
Flutter supports deep linking on iOS, Android, and the web.
Opening a URL displays that screen in your app.
With the following steps,
you can launch and display routes by using named routes
(either with the routes parameter or
onGenerateRoute), or by
using the Router widget.
:::note
Named routes are no longer recommended for most
applications. For more information, see
Limitations in the navigation overview page.
:::
If you're running the app in a web browser, there's no additional setup
required. Route paths are handled in the same way as an iOS or Android deep
link. By default, web apps read the deep link path from the url fragment using
the pattern: /#/path/to/app/screen, but this can be changed by
configuring the URL strategy for your app.
If you are a visual learner, check out the following video:

To get started, see our cookbooks for Android and iOS:




        Android
      





        iOS
