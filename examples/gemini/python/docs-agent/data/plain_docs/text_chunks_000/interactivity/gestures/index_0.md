This document explains how to listen for, and respond to,
gestures in Flutter.
Examples of gestures include taps, drags, and scaling.
The gesture system in Flutter has two separate layers.
The first layer has raw pointer events that describe
the location and movement of pointers (for example,
touches, mice, and styli) across the screen.
The second layer has gestures that describe semantic
actions that consist of one or more pointer movements.
Pointers represent raw data about the user's interaction
with the device's screen.
There are four types of pointer events:
PointerDownEvent
: The pointer has contacted the screen at a particular location.
PointerMoveEvent
: The pointer has moved from one location on the screen to another.
PointerUpEvent
: The pointer has stopped contacting the screen.
PointerCancelEvent
: Input from this pointer is no longer directed towards this app.
On pointer down, the framework does a hit test on your app
to determine which widget exists at the location where the
pointer contacted the screen. The pointer down event
(and subsequent events for that pointer) are then dispatched
to the innermost widget found by the hit test.
From there, the events bubble up the tree and are dispatched
to all the widgets on the path from the innermost
widget to the root of the tree. There is no mechanism for
canceling or stopping pointer events from being dispatched further.
To listen to pointer events directly from the widgets layer, use a
Listener widget. However, generally,
consider using gestures (as discussed below) instead.
