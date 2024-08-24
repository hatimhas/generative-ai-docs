Although named routes can handle deep links, the behavior is always the same and
can't be customized. When a new deep link is received by the platform, Flutter
pushes a new Route onto the Navigator regardless of where the user currently is.
Flutter also doesn't support the browser forward button for applications using
named routes. For these reasons, we don't recommend using named routes in most
applications.
