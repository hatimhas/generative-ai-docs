After calling createState() on the StatefulWidget,
the framework inserts the new state object into the tree and
then calls initState() on the state object.
A subclass of State can override initState to do work
that needs to happen just once. For example, override initState
to configure animations or to subscribe to platform services.
Implementations of initState are required to start
by calling super.initState.
When a state object is no longer needed,
the framework calls dispose() on the state object.
Override the dispose function to do cleanup work.
For example, override dispose to cancel timers or to
unsubscribe from platform services. Implementations of
dispose typically end by calling super.dispose.
For more information, check out State.
