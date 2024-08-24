Flutter applications with advanced navigation and routing requirements (such as
a web app that uses direct links to each screen, or an app with multiple
Navigator widgets) should use a routing package such as go_router that can
parse the route path and configure the Navigator whenever the app receives a
new deep link.
To use the Router, switch to the router constructor on MaterialApp or
CupertinoApp and provide it with a Router configuration. Routing packages,
such as go_router, typically provide a
configuration for you. For example:
dart
MaterialApp.router(
  routerConfig: GoRouter(
    // …
  )
);
Because packages like go_router are declarative, they will always display the
same screen(s) when a deep link is received.
:::note Note for advanced developers
If you prefer not to use a routing package
and would like full control over navigation and routing in your app, override
RouteInformationParser and RouterDelegate. When the state in your app
changes, you can precisely control the stack of screens by providing a list of
Page objects using the Navigator.pages parameter. For more details, see the
Router API documentation.
:::
