Use keys to control which widgets the framework matches up
with other widgets when a widget rebuilds. By default, the
framework matches widgets in the current and previous build
according to their runtimeType and the order in which they appear.
With keys, the framework requires that the two widgets have
the same key as well as the same runtimeType.
Keys are most useful in widgets that build many instances of
the same type of widget. For example, the ShoppingList widget,
which builds just enough ShoppingListItem instances to
fill its visible region:


Without keys, the first entry in the current build
   would always sync with the first entry in the previous build,
   even if, semantically, the first entry in the list just
   scrolled off screen and is no longer visible in the viewport.


By assigning each entry in the list a "semantic" key,
   the infinite list can be more efficient because the
   framework syncs entries with matching semantic keys
   and therefore similar (or identical) visual appearances.
   Moreover, syncing the entries semantically means that
   state retained in stateful child widgets remains attached
   to the same semantic entry rather than the entry in the
   same numerical position in the viewport.


For more information, check out the Key API.
