This page describes how to bind physical keyboard events to actions in the user
interface. For instance, to define keyboard shortcuts in your application, this
page is for you.
For a GUI application to do anything, it has to have actions: users want to tell
the application to do something. Actions are often simple functions that
directly perform the action (such as set a value or save a file). In a larger
application, however, things are more complex: the code for invoking the action,
and the code for the action itself might need to be in different places.
Shortcuts (key bindings) might need definition at a level that knows nothing
about the actions they invoke.
That's where Flutter's actions and shortcuts system comes in. It allows
developers to define actions that fulfill intents bound to them. In this
context, an intent is a generic action that the user wishes to perform, and an
Intent class instance represents these user intents in Flutter. An
Intent can be general purpose, fulfilled by different actions in different
contexts. An Action can be a simple callback (as in the case of
the CallbackAction) or something more complex that integrates with entire
undo/redo architectures (for example) or other logic.
!Using Shortcuts Diagram
Shortcuts are key bindings that activate by pressing a key or combination
of keys. The key combinations reside in a table with their bound intent. When
the Shortcuts widget invokes them, it sends their matching intent to the
actions subsystem for fulfillment.
To illustrate the concepts in actions and shortcuts, this article creates a
simple app that allows a user to select and copy text in a text field using both
buttons and shortcuts.
