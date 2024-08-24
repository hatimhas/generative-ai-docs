You can use the GridView widget to transform
your existing ListView into more reasonably-sized items.
GridView is similar to the ListView widget,
but instead of handling only a list of widgets arranged linearly,
GridView can arrange widgets in a two-dimensional array.
GridView also has constructors that are similar to ListView.
The ListView default constructor maps to GridView.count,
and ListView.builder is similar to GridView.builder.
GridView has some additional constructors for more custom layouts.
To learn more, visit the GridView API page.
For example, if your original app used a ListView.builder,
swap that out for a GridView.builder.
If your app has a large number of items,
it's recommended to use this builder constructor to only
build the item widgets that are actually visible.
Most of the parameters in the constructor are the same between
the two widgets, so it's a straightforward swap.
However, you need to figure out what to set for the gridDelegate.
Flutter provides powerful premade gridDelegates
that you can use, namely:
SliverGridDelegateWith<b>FixedCrossAxisCount</b>
: Lets you assign a specific number of columns to your grid.
SliverGridDelegateWith<b>MaxCrossAxisExtent</b> 
: Lets you define a max item width.
:::secondary
Don't use the grid delegate for these classes that lets
you set the column count directly and then hardcode
the number of columns based on whether the device
is a tablet, or whatever. 
The number of columns should be based on the size of
the window and not the size of the physical device.
This distinction is important because many mobile
devices support multi-window mode, which can
cause your app to be rendered in a space smaller than
the physical size of the display. Also, Flutter apps
can run on web and desktop, which might be sized in many ways.
For this reason, use MediaQuery to get the app window size
rather than the physical device size.
:::
