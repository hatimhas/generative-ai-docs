Don't lock the orientation of your app.
An adaptive app should look good on windows of
different sizes and shapes. While locking an app
to portrait mode on phones can help narrow the scope
of a minimum viable product, it can increase the
effort required to make the app adaptive in the future.
For example, the assumption that phones will only
render your app in a full screen portrait mode is
not a guarantee. Multi window app support is becoming common,
and foldables have many use cases that work best with
multiple apps running side by side.
If you absolutely must lock your app in portrait mode (but don't),
use the Display API instead of something like MediaQuery
to get the physical dimensions of the screen.
To summarize:

Locked screens can be an accessibility issue for some users
Android large format tiers require portrait and landscape
    support at the lowest level.
Android devices can override a locked screen
Apple guidelines say aim to support both orientations
