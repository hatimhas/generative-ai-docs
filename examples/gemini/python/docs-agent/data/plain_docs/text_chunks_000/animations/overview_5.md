Animations are actually built from a number of core building blocks.
Scheduler
The SchedulerBinding is a singleton class
that exposes the Flutter scheduling primitives.
For this discussion, the key primitive is the frame callbacks.
Each time a frame needs to be shown on the screen,
Flutter's engine triggers a "begin frame" callback that
the scheduler multiplexes to all the listeners registered using
scheduleFrameCallback(). All these callbacks are
given the official time stamp of the frame, in
the form of a Duration from some arbitrary epoch. Since all the
callbacks have the same time, any animations triggered from these
callbacks will appear to be exactly synchronised even
if they take a few milliseconds to be executed.
