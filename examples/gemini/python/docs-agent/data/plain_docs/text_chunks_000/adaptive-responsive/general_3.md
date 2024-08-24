LayoutBuilder accomplishes a similar goal as
MediaQuery.sizeOf, with some distinctions.
Rather than providing the size of the app's window,
LayoutBuilder provides the layout constraints from
the parent Widget. This means that you get
sizing information based on the specific spot
in the widget tree where you added the LayoutBuilder.
Also, LayoutBuilder returns a BoxConstraints
object instead of a Size object,
so you are given the valid width
and height ranges (minimum and maximum) for the content,
rather than just a fixed size.
This can be useful for custom widgets.
For example, imagine a custom widget, where you want
the sizing to be based on the space specifically
given to that widget, and not the app window in general.
In this scenario, use LayoutBuilder.
