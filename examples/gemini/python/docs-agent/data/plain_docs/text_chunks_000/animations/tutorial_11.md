:::secondary What's the point?
* An AnimatedBuilder understands how to render the transition.
* An AnimatedBuilder doesn't know how to render the widget,
  nor does it manage the Animation object.
* Use AnimatedBuilder to describe an animation as
  part of a build method for another widget.
  If you simply want to define a widget with a reusable
  animation, use an AnimatedWidget, as shown in
  the Simplifying with AnimatedWidget section.
* Examples of AnimatedBuilders in the Flutter API: BottomSheet,
  ExpansionTile, PopupMenu, ProgressIndicator,
  RefreshIndicator, Scaffold, SnackBar, TabBar,
  TextField.
:::
One problem with the code in the animate3 example,
is that changing the animation required changing the widget
that renders the logo. A better solution
is to separate responsibilities into different classes:

Render the logo
Define the Animation object
Render the transition

You can accomplish this separation with the help of the
AnimatedBuilder class. An AnimatedBuilder is a
separate class in the render tree. Like AnimatedWidget,
AnimatedBuilder automatically listens to notifications
from the Animation object, and marks the widget tree
dirty as necessary, so you don't need to call addListener().
The widget tree for the animate4
example looks like this:

Starting from the bottom of the widget tree, the code for rendering
the logo is straightforward:
code-excerpt "animate4/lib/main.dart (logo-widget)"?
```dart
class LogoWidget extends StatelessWidget {
  const LogoWidget();
// Leave out the height and width so it fills the animating parent.
  @override
  Widget build(BuildContext context) {
    return Container(
      margin: const EdgeInsets.symmetric(vertical: 10),
      child: const FlutterLogo(),
    );
  }
}
```
The middle three blocks in the diagram are all created in the
build() method in GrowTransition, shown below.
The GrowTransition widget itself is stateless and holds
the set of final variables necessary to define the transition animation.
The build() function creates and returns the AnimatedBuilder,
which takes the (Anonymous builder) method and the
LogoWidget object as parameters. The work of rendering the
transition actually happens in the (Anonymous builder)
method, which creates a Container of the appropriate size
to force the LogoWidget to shrink to fit.
One tricky point in the code below is that the child looks
like it's specified twice. What's happening is that the
outer reference of child is passed to AnimatedBuilder,
which passes it to the anonymous closure, which then uses
that object as its child. The net result is that the
AnimatedBuilder is inserted in between the two widgets
in the render tree.
code-excerpt "animate4/lib/main.dart (grow-transition)"?
```dart
class GrowTransition extends StatelessWidget {
  const GrowTransition({
    required this.child,
    required this.animation,
    super.key,
  });
final Widget child;
  final Animation animation;
@override
  Widget build(BuildContext context) {
    return Center(
      child: AnimatedBuilder(
        animation: animation,
        builder: (context, child) {
          return SizedBox(
            height: animation.value,
            width: animation.value,
            child: child,
          );
        },
        child: child,
      ),
    );
  }
}
```
Finally, the code to initialize the animation looks very
similar to the animate2 example. The initState()
method creates an AnimationController and a Tween,
then binds them with animate(). The magic happens in
the build() method, which returns a GrowTransition
object with a LogoWidget as a child, and an animation object to
drive the transition. These are the three elements listed
in the bullet points above.
```dart diff
  void main() => runApp(const LogoApp());

class LogoWidget extends StatelessWidget {
const LogoWidget();

// Leave out the height and width so it fills the animating parent.
@override
Widget build(BuildContext context) {
return Container(
margin: const EdgeInsets.symmetric(vertical: 10),
child: const FlutterLogo(),
);
}
}

class GrowTransition extends StatelessWidget {
const GrowTransition({
required this.child,
required this.animation,
super.key,
});

final Widget child;
final Animation animation;

@override
Widget build(BuildContext context) {
final animation = listenable as Animation;
return Center(
child: Container(
margin: const EdgeInsets.symmetric(vertical: 10),
height: animation.value,
width: animation.value,
child: const FlutterLogo(),
child: AnimatedBuilder(
animation: animation,
builder: (context, child) {
return SizedBox(
height: animation.value,
width: animation.value,
child: child,
);
},
child: child,
),
);
}
}

class LogoApp extends StatefulWidget {
    // ...
@override


Widget build(BuildContext context) => AnimatedLogo(animation: animation);
Widget build(BuildContext context) {
return GrowTransition(
animation: animation,
child: const LogoWidget(),
);

}
// ...
  }
```


App source: animate4
