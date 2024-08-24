code-excerpt path-base="ui/adaptive_app_demos"?
So, just how do you approach taking an app
designed for conventional mobile devices,
and make it beautiful on a wide range
of devices? What steps are required?
Google engineers, who have experience doing this
very thing for large apps, recommend the
following 3-step approach.

First, identify the widgets that you plan to
make dynamic. Analyze the constructors for those
widgets and abstract out the data that you can share.
Common widgets that require adaptibility are:

Dialogs, both fullscreen and modal
Navigation UI, both rail and bottom bar
Custom layout, such as "is the UI area taller or wider?"

For example, in a Dialog widget, you can share
the info that contains the content of the dialog.
Or, perhaps you want to switch between a
NavigationBar when the app window is small,
and a NavigationRail when the app window is large.
These widgets would likely share a list of
navigable destinations. In this case,
you might create a Destination widget to hold
this info, and specify the Destination as having both
an icon and a text label.
Next, you will evaluate your screen size to decide
on how to display your UI.
