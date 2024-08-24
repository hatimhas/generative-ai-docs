You might wonder: why not just map a key combination directly to an action?  Why
have intents at all? This is because it is useful to have a separation of
concerns between where the key mapping definitions are (often at a high level),
and where the action definitions are (often at a low level), and because it is
important to be able to have a single key combination map to an intended
operation in an app, and have it adapt automatically to whichever action
fulfills that intended operation for the focused context.
For instance, Flutter has an ActivateIntent widget that maps each type of
control to its corresponding version of an ActivateAction (and that executes
the code that activates the control). This code often needs fairly private
access to do its work. If the extra layer of indirection that Intents provide
didn't exist, it would be necessary to elevate the definition of the actions to
where the defining instance of the Shortcuts widget could see them, causing
the shortcuts to have more knowledge than necessary about which action to
invoke, and to have access to or provide state that it wouldn't necessarily have
or need otherwise. This allows your code to separate the two concerns to be more
independent.
Intents configure an action so that the same action can serve multiple uses. An
example of this is DirectionalFocusIntent, which takes a direction to move
the focus in, allowing the DirectionalFocusAction to know which direction to
move the focus. Just be careful: don't pass state in the Intent that applies
to all  invocations of an Action: that kind of state should be passed to the
constructor of the Action itself, to keep the Intent from needing to know
too much.
