The custom PhotoHero class maintains the hero,
and its size, image, and behavior when tapped.
The PhotoHero builds the following widget tree:


  ![PhotoHero class widget tree](/assets/images/docs/ui/animations/photohero-class.png)


Here's the code:
```dart
class PhotoHero extends StatelessWidget {
  const PhotoHero({
    super.key,
    required this.photo,
    this.onTap,
    required this.width,
  });
final String photo;
  final VoidCallback? onTap;
  final double width;
@override
  Widget build(BuildContext context) {
    return SizedBox(
      width: width,
      child: Hero(
        tag: photo,
        child: Material(
          color: Colors.transparent,
          child: InkWell(
            onTap: onTap,
            child: Image.asset(
              photo,
              fit: BoxFit.contain,
            ),
          ),
        ),
      ),
    );
  }
}
```
Key information:

The starting route is implicitly pushed by MaterialApp when
  HeroAnimation is provided as the app's home property.
An InkWell wraps the image, making it trivial to add a tap
  gesture to the both the source and destination heroes.
Defining the Material widget with a transparent color
  enables the image to "pop out" of the background as it
  flies to its destination.
The SizedBox specifies the hero's size at the start and
  end of the animation.
Setting the Image's fit property to BoxFit.contain,
  ensures that the image is as large as possible during the
  transition without changing its aspect ratio.
