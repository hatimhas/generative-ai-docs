Material Design is an open-source design system built
and supported by Google designers and developers.
The latest version, Material 3, enables personal,
adaptive, and expressive experiences—from dynamic color
and enhanced accessibility, to foundations for
large screen layouts, and design tokens.
:::warning
As of the Flutter 3.16 release, Material 3 is
enabled by default. For now, you can opt out
of Material 3 by setting the useMaterial3 property
to false. But be aware that the useMaterial3
property and support for Material 2
will eventually be deprecated according to
Flutter's deprecation policy.
:::
For most Flutter widgets, upgrading to Material 3
is seamless. But some widgets couldn't be
updated—entirely new implementations were needed,
such as NavigationBar.
You must make these changes to your code manually.
Until your app is entirely updated,
the UI might look or act a bit strange.
You can find the entirely new Material components by
visiting the Affected widgets page.
Explore the updated components, typography, color system,
and elevation support with the
interactive Material 3 demo:

To learn more about Material Design and Flutter,
check out:

Material.io developer documentation
Migrating a Flutter app to Material 3 blog post by Taha Tesser
Umbrella issue on GitHub
