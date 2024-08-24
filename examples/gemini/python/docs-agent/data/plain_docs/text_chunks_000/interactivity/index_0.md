:::secondary What you'll learn
* How to respond to taps.
* How to create a custom widget.
* The difference between stateless and stateful widgets.
:::
How do you modify your app to make it react to user input?
In this tutorial, you'll add interactivity to an app that
contains only non-interactive widgets.
Specifically, you'll modify an icon to make it tappable
by creating a custom stateful widget that manages two
stateless widgets.
The building layouts tutorial showed you how to create
the layout for the following screenshot.

When the app first launches, the star is solid red,
indicating that this lake has previously been favorited.
The number next to the star indicates that 41
people have favorited this lake. After completing this tutorial,
tapping the star removes its favorited status,
replacing the solid star with an outline and
decreasing the count. Tapping again favorites the lake,
drawing a solid star and increasing the count.

To accomplish this, you'll create a single custom widget
that includes both the star and the count,
which are themselves widgets. Tapping the star changes state
for both widgets, so the same widget should manage both.
You can get right to touching the code in
Step 2: Subclass StatefulWidget.
If you want to try different ways of managing state,
skip to Managing state.
A widget is either stateful or stateless. If a widget can
change—when a user interacts with it,
for example—it's stateful.
A stateless widget never changes.
Icon, IconButton, and Text are
examples of stateless widgets. Stateless widgets
subclass StatelessWidget.
A stateful widget is dynamic: for example,
it can change its appearance in response to events
triggered by user interactions or when it receives data.
Checkbox, Radio, Slider,
InkWell, Form, and TextField
are examples of stateful widgets. Stateful widgets
subclass StatefulWidget.
A widget's state is stored in a State object,
separating the widget's state from its appearance.
The state consists of values that can change, like a
slider's current value or whether a checkbox is checked.
When the widget's state changes,
the state object calls setState(),
telling the framework to redraw the widget.
