}/tree/}/examples 
code-excerpt path-base=""?
dl, dd 
:::secondary What's the point?
* Widgets are classes used to build UIs.
* Widgets are used for both layout and UI elements.
* Compose simple widgets to build complex widgets.
:::
The core of Flutter's layout mechanism is widgets.
In Flutter, almost everything is a widget—even
layout models are widgets. The images, icons,
and text that you see in a Flutter app are all widgets.
But things you don't see are also widgets,
such as the rows, columns, and grids that arrange,
constrain, and align the visible widgets.
You create a layout by composing widgets to build more complex widgets.
For example, the first screenshot below shows 3 icons with a label
under each one:






The second screenshot displays the visual layout, showing a row of
3 columns where each column contains an icon and a label.
:::note
Most of the screenshots in this tutorial are displayed with
debugPaintSizeEnabled set to true so you can see the visual layout.
For more information, see
Debugging layout issues visually, a section in
Using the Flutter inspector.
:::
Here's a diagram of the widget tree for this UI:

Most of this should look as you might expect, but you might be wondering
about the containers (shown in pink). Container is a widget class
that allows you to customize its child widget. Use a Container when
you want to add padding, margins, borders, or background color,
to name some of its capabilities.
In this example, each Text widget is placed in a Container
to add margins. The entire Row is also placed in a
Container to add padding around the row.
The rest of the UI in this example is controlled by properties.
Set an Icon's color using its color property.
Use the Text.style property to set the font, its color, weight, and so on.
Columns and rows have properties that allow you to specify how their
children are aligned vertically or horizontally, and how much space
the children should occupy.
How do you lay out a single widget in Flutter? This section
shows you how to create and display a simple widget.
It also shows the entire code for a simple Hello World app.
In Flutter, it takes only a few steps to put text, an icon,
or an image on the screen.
