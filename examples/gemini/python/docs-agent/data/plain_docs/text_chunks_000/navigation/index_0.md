Flutter provides a complete system for navigating between screens and handling
deep links. Small applications without complex deep linking can use
Navigator, while apps with specific deep linking and navigation
requirements should also use the Router to correctly handle deep links on
Android and iOS, and to stay in sync with the address bar when the app is
running on the web.
To configure your Android or iOS application to handle deep links, see 
Deep linking.
The Navigator widget displays screens as a stack using the correct transition
animations for the target platform. To navigate to a new screen, access the
Navigator through the route's BuildContext and call imperative methods such
as push() or pop():
dart
onPressed: () {
  Navigator.of(context).push(
    MaterialPageRoute(
      builder: (context) => const SongScreen(song: song),
    ),
  );
},
child: Text(song.name),
Because Navigator keeps a stack of Route objects (representing the history
stack), The push() method also takes a Route object. The MaterialPageRoute
object is a subclass of Route that specifies the transition animations for
Material Design. For more examples of how to use the Navigator, follow the
navigation recipes from the Flutter Cookbook or visit the [Navigator API
documentation][Navigator].
