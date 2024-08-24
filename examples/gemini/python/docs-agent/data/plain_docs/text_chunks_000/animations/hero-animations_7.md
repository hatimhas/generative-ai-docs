The HeroAnimation class creates the source and destination
PhotoHeroes, and sets up the transition.
Here's the code:
```dart
class HeroAnimation extends StatelessWidget {
  const HeroAnimation();
Widget build(BuildContext context) {
    [!timeDilation = 5.0; // 1.0 means normal animation speed.!]
return Scaffold(
  appBar: AppBar(
    title: const Text('Basic Hero Animation'),
  ),
  body: Center(
    [!child: PhotoHero(!]
      photo: 'images/flippers-alpha.png',
      width: 300.0,
      [!onTap: ()!] {
        [!Navigator.of(context).push(MaterialPageRoute<void>(!]
          [!builder: (context)!] {
            return Scaffold(
              appBar: AppBar(
                title: const Text('Flippers Page'),
              ),
              body: Container(
                // Set background to blue to emphasize that it's a new route.
                color: Colors.lightBlueAccent,
                padding: const EdgeInsets.all(16),
                alignment: Alignment.topLeft,
                [!child: PhotoHero(!]
                  photo: 'images/flippers-alpha.png',
                  width: 100.0,
                  [!onTap: ()!] {
                    [!Navigator.of(context).pop();!]
                  },
                ),
              ),
            );
          }
        ));
      },
    ),
  ),
);

}
}
```
Key information:

When the user taps the InkWell containing the source hero,
  the code creates the destination route using MaterialPageRoute.
  Pushing the destination route to the Navigator's stack triggers
  the animation.
The Container positions the PhotoHero in the destination
  route's top-left corner, below the AppBar.
The onTap() method for the destination PhotoHero
  pops the Navigator's stack, triggering the animation
  that flies the Hero back to the original route.
Use the timeDilation property to slow the transition
  while debugging.
