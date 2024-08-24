dl, dd 
:::secondary What you'll learn
* How to lay out widgets next to each other.
* How to add space between widgets.
* How adding and nesting widgets results in a Flutter layout.
:::
This tutorial explains how to design and build layouts in Flutter.
If you use the example code provided, you can build the following app.



Photo by Dino Reichmuth on Unsplash.
Text by Switzerland Tourism.


To get a better overview of the layout mechanism, start with
Flutter's approach to layout.
In this section, consider what type of user experience you want for
your app users.
Consider how to position the components of your user interface.
A layout consists of the total end result of these positionings.
Consider planning your layout to speed up your coding.
Using visual cues to know where something goes on screen can be a great help.
Use whichever method you prefer, like an interface design tool or a pencil
and a sheet of paper. Figure out where you want to place elements on your
screen before writing code. It's the programming version of the adage:
"Measure twice, cut once."



Ask these questions to break the layout down to its basic elements.

* Can you identify the rows and columns?
* Does the layout include a grid?
* Are there overlapping elements?
* Does the UI need tabs?
* What do you need to align, pad, or border?




Identify the larger elements. In this example, you arrange the image, title,
buttons, and description into a column.






Diagram each row.




Row 1, the **Title** section, has three children:
a column of text, a star icon, and a number.
Its first child, the column, contains two lines of text.
That first column might need more space.






Row 2, the **Button** section, has three children: each child contains
a column which then contains an icon and text.



  



After diagramming the layout, consider how you would code it.
Would you write all the code in one class?
Or, would you create one class for each part of the layout?
To follow Flutter best practices, create one class, or Widget,
to contain each part of your layout.
When Flutter needs to re-render part of a UI,
it updates the smallest part that changes.
This is why Flutter makes "everything a widget".
If only the text changes in a Text widget, Flutter redraws only that text.
Flutter changes the least amount of the UI possible in response to user input.
For this tutorial, write each element you have identified as its own widget.
