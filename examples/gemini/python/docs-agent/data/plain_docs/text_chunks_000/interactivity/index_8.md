:::secondary What's the point?
* There are different approaches for managing state.
* You, as the widget designer, choose which approach to use.
* If in doubt, start by managing state in the parent widget.
:::
Who manages the stateful widget's state? The widget itself?
The parent widget?  Both? Another object?
The answer is... it depends. There are several valid ways
to make your widget interactive. You, as the widget designer,
make the decision based on how you expect your widget to be used.
Here are the most common ways to manage state:

The widget manages its own state
The parent manages the widget's state
A mix-and-match approach

How do you decide which approach to use?
The following principles should help you decide:


If the state in question is user data,
  for example the checked or unchecked
  mode of a checkbox, or the position of a slider,
  then the state is best managed by the parent widget.


If the state in question is aesthetic,
  for example an animation, then the
  state is best managed by the widget itself.


If in doubt, start by managing state in the parent widget.
We'll give examples of the different ways of managing state
by creating three simple examples: TapboxA, TapboxB,
and TapboxC. The examples all work similarly—each
creates a container that, when tapped, toggles between a
green or grey box. The _active boolean determines the
color: green for active or grey for inactive.






These examples use GestureDetector to capture activity
on the Container.
