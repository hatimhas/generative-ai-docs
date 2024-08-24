The behavior varies slightly based on the platform and whether the app is
launched and running.
| Platform / Scenario      | Using Navigator                                                     | Using Router                                                                                                                                                                                               |
|--------------------------|---------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| iOS (not launched)       | App gets initialRoute ("/") and a short time after gets a pushRoute | App gets initialRoute ("/") and a short time after uses the RouteInformationParser to parse the route and call RouterDelegate.setNewRoutePath, which configures the Navigator with the corresponding Page. |
| Android - (not launched) | App gets initialRoute containing the route ("/deeplink")            | App gets initialRoute ("/deeplink") and passes it to the RouteInformationParser to parse the route and call RouterDelegate.setNewRoutePath, which configures the Navigator with the corresponding Pages.   |
| iOS (launched)           | pushRoute is called                                                 | Path is parsed, and the Navigator is configured with a new set of Pages.                                                                                                                                   |
| Android (launched)       | pushRoute is called                                                 | Path is parsed, and the Navigator is configured with a new set of Pages.                                                                                                                                   |

When using the Router widget,
your app has the ability to replace the
current set of pages when a new deep link
is opened while the app is running.
