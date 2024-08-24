At a given location on screen,
there might be multiple gesture detectors.
For example:

A ListTile has a tap recognizer that responds
  to the entire ListTile, and a nested one around
  a trailing icon button. The screen rect of the
  trailing icon is now covered by two gesture
  recognizers that need to negotiate for who handles
  the gesture if it turns out to be a tap.
A single GestureDetector covers a screen area
  configured to handle multiple gestures,
  such as a long press and a tap.
  The tap recognizer must now negotiate
  with the long press recognizer when
  the user touches that part of the screen.
  Depending on what happens next with that pointer,
  one of the two recognizers receives the gesture,
  or neither receives the gesture if the user
  performs something that's neither a tap nor a long press.

All of these gesture detectors listen to the stream
of pointer events as they flow past and attempt to recognize
specific gestures. The [GestureDetector] widget decides
which gestures to attempt to recognize based on which of its
callbacks are non-null.
When there is more than one gesture recognizer for a given
pointer on the screen, the framework disambiguates which
gesture the user intends by having each recognizer join
the gesture arena. The gesture arena determines which
gesture wins using the following rules:


At any time, a recognizer can eliminate itself and leave the
  arena. If there's only one recognizer left in the arena,
  that recognizer wins.


At any time, a recognizer can declare itself the winner,
  causing all of the remaining recognizers to lose.


For example, when disambiguating horizontal and vertical dragging,
both recognizers enter the arena when they receive the pointer
down event. The recognizers observe the pointer move events.
If the user moves the pointer more than a certain number of
logical pixels horizontally, the horizontal recognizer declares
the win and the gesture is interpreted as a horizontal drag.
Similarly, if the user moves more than a certain number of logical
pixels vertically, the vertical recognizer declares itself the winner.
The gesture arena is beneficial when there is only a horizontal
(or vertical) drag recognizer. In that case, there is only one
recognizer in the arena and the horizontal drag is recognized
immediately, which means the first pixel of horizontal movement
can be treated as a drag and the user won't need to wait for
further gesture disambiguation.
