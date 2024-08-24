You might consider enlarging the "hit area"
of a widget to accommodate a touch screen, for example.
Different input devices offer various levels of precision,
which necessitate differently-sized hit areas.
Flutter's VisualDensity class makes it easy to adjust the
density of your views across the entire application,
for example, by making a button larger
(and therefore easier to tap) on a touch device.
When you change the VisualDensity for
your MaterialApp, MaterialComponents
that support it animate their densities to match.
By default, both horizontal and vertical densities
are set to 0.0, but you can set the densities to any
negative or positive value that you want.
By switching between different
densities, you can easily adjust your UI.

To set a custom visual density,
inject the density into your MaterialApp theme:
code-excerpt "lib/main.dart (visual-density)"?
dart
double densityAmt = touchMode ? 0.0 : -1.0;
VisualDensity density =
    VisualDensity(horizontal: densityAmt, vertical: densityAmt);
return MaterialApp(
  theme: ThemeData(visualDensity: density),
  home: MainAppScaffold(),
  debugShowCheckedModeBanner: false,
);
To use VisualDensity inside your own views,
you can look it up:
code-excerpt "lib/pages/adaptive_reflow_page.dart (visual-density-own-view)"?
dart
VisualDensity density = Theme.of(context).visualDensity;
Not only does the container react automatically to changes
in density, it also animates when it changes.
This ties together your custom components,
along with the built-in components,
for a smooth transition effect across the app.
As shown, VisualDensity is unit-less,
so it can mean different things to different views.
In the following example, 1 density unit equals 6 pixels,
but this is totally up to you to decide.
The fact that it is unit-less makes it quite versatile,
and it should work in most contexts.
It's worth noting that the Material generally
use a value of around 4 logical pixels for each
visual density unit. For more information about the
supported components, see the VisualDensity API.
For more information about density principles in general,
see the Material Design guide.
