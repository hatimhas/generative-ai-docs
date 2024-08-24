PENDING: Reid, I think you suggested renaming/removing this item? I can't, for the life of me, find that comment in the PR

To maintain the scroll position in a list
that doesn't change its layout when the
device's orientation changes,
use the PageStorageKey class.
PageStorageKey persists the
widget state in storage after the widget is
destroyed and restores state when recreated.
You can see an example of this in the Wonderous app,
where it stores the list's state in the
SingleChildScrollView widget.
If the List widget changes its layout
when the device's orientation changes,
you might have to do a bit of math (example)
to change the scroll position on screen rotation.
