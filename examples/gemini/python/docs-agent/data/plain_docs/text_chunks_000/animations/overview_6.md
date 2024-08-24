The Ticker class hooks into the scheduler's
scheduleFrameCallback()
mechanism to invoke a callback every tick.
A Ticker can be started and stopped. When started,
it returns a Future that will resolve when it is stopped.
Each tick, the Ticker provides the callback with the
duration since the first tick after it was started. 
Because tickers always give their elapsed time relative to the first
tick after they were started; tickers are all synchronised. If you
start three tickers at different times between two ticks, they will all
nonetheless be synchronised with the same starting time, and will
subsequently tick in lockstep. Like people at a bus-stop,
all the tickers wait for a regularly occurring event
(the tick) to begin moving (counting time).
