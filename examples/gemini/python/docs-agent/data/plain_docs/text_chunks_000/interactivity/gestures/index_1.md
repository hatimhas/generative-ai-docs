Gestures represent semantic actions (for example, tap, drag,
and scale) that are recognized from multiple individual pointer
events, potentially even multiple individual pointers.
Gestures can dispatch multiple events, corresponding to the
lifecycle of the gesture (for example, drag start,
drag update, and drag end):
Tap
onTapDown
: A pointer that might cause a tap has contacted
  the screen at a particular location.
onTapUp
: A pointer that triggers a tap has stopped contacting
  the screen at a particular location.
onTap
: The pointer that previously triggered the onTapDown
  has also triggered onTapUp which ends up causing a tap.
onTapCancel
: The pointer that previously triggered the onTapDown
  won't end up causing a tap.
Double tap
onDoubleTap
: The user has tapped the screen at the same location twice in
  quick succession.
Long press
onLongPress
: A pointer has remained in contact with the
  screen at the same location for a long period of time.
Vertical drag
onVerticalDragStart
: A pointer has contacted the screen and might begin to
  move vertically.
onVerticalDragUpdate
: A pointer that is in contact with the screen and
    moving vertically has moved in the vertical direction.
onVerticalDragEnd
: A pointer that was previously in contact with the screen
    and moving vertically is no longer in contact with the
    screen and was moving at a specific velocity when it
    stopped contacting the screen.
Horizontal drag
onHorizontalDragStart
: A pointer has contacted the screen and might begin to
  move horizontally.
onHorizontalDragUpdate
: A pointer that is in contact with the screen and
  moving horizontally has moved in the horizontal direction.
onHorizontalDragEnd
: A pointer that was previously in contact with the
  screen and moving horizontally is no longer in contact
  with the screen and was moving at a specific velocity
  when it stopped contacting the screen.
Pan
onPanStart
: A pointer has contacted the screen and might begin to move
  horizontally or vertically. This callback crashes if
  onHorizontalDragStart or onVerticalDragStart is set.
onPanUpdate
: A pointer that is in contact with the screen and is moving
  in the vertical or horizontal direction. This callback
  crashes if onHorizontalDragUpdate or onVerticalDragUpdate
  is set.
onPanEnd
: A pointer that was previously in contact with screen
  is no longer in contact with the screen and is moving
  at a specific velocity when it stopped contacting the screen.
  This callback crashes if onHorizontalDragEnd or
  onVerticalDragEnd is set.
