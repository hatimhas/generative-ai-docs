PathUrlStrategy uses the History API, which requires additional
configuration for web servers.
To configure your web server to support PathUrlStrategy, check your web server's
documentation to rewrite requests to index.html.Check your web server's
documentation for details on how to configure single-page apps.
If you are using Firebase Hosting, choose the "Configure as a single-page app"
option when initializing your project. For more information see Firebase's
Configure rewrites documentation.
The local dev server created by running flutter run -d chrome is configured to
handle any path gracefully and fallback to your app's index.html file.
