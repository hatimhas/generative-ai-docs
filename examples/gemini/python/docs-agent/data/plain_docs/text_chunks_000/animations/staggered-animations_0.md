:::secondary What you'll learn
* A staggered animation consists of sequential or overlapping
    animations.
* To create a staggered animation, use multiple Animation objects.
* One AnimationController controls all of the Animations.
* Each Animation object specifies the animation during an Interval.
* For each property being animated, create a Tween.
:::
:::tip Terminology
If the concept of tweens or tweening is new to you, see the
Animations in Flutter tutorial.
:::
Staggered animations are a straightforward concept: visual changes
happen as a series of operations, rather than all at once.
The animation might be purely sequential, with one change occurring after
the next, or it might partially or completely overlap. It might also
have gaps, where no changes occur.
This guide shows how to build a staggered animation in Flutter.
:::secondary Examples
This guide explains the basic_staggered_animation example.
You can also refer to a more complex example,
staggered_pic_selection.
basic_staggered_animation
: Shows a series of sequential and overlapping animations
  of a single widget. Tapping the screen begins an animation
  that changes opacity, size, shape, color, and padding.
staggered_pic_selection
: Shows deleting an image from a list of images displayed
  in one of three sizes. This example uses two
  animation controllers: one for image selection/deselection,
  and one for image deletion. The selection/deselection
  animation is staggered. (To see this effect,
  you might need to increase the timeDilation value.)
  Select one of the largest images—it shrinks as it
  displays a checkmark inside a blue circle.
  Next, select one of the smallest images—the
  large image expands as the checkmark disappears.
  Before the large image has finished expanding,
  the small image shrinks to display its checkmark.
  This staggered behavior is similar to what you might
  see in Google Photos.
:::
The following video demonstrates the animation performed by
basic_staggered_animation:
In the video, you see the following animation of a single widget,
which begins as a bordered blue square with slightly rounded corners.
The square runs through changes in the following order:
Fades in
Widens
Becomes taller while moving upwards
Transforms into a bordered circle
Changes color to orange
After running forward, the animation runs in reverse.
:::secondary New to Flutter?
This page assumes you know how to create a layout using Flutter's
widgets.  For more information, see Building Layouts in Flutter.
:::
:::secondary What's the point?
* All of the animations are driven by the same
    AnimationController.
* Regardless of how long the animation lasts in real time,
    the controller's values must be between 0.0 and 1.0, inclusive.
* Each animation has an Interval
    between 0.0 and 1.0, inclusive.
* For each property that animates in an interval, create a
    Tween. The Tween specifies the start and end
    values for that property.
* The Tween produces an Animation
    object that is managed by the controller.
