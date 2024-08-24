An Animation object can have Listeners and StatusListeners,
defined with addListener() and addStatusListener().
A Listener is called whenever the value of the animation changes.
The most common behavior of a Listener is to call setState()
to cause a rebuild. A StatusListener is called when an animation begins,
ends, moves forward, or moves reverse, as defined by AnimationStatus.
The next section has an example of the addListener() method,
and Monitoring the progress of the animation shows an
example of addStatusListener().
