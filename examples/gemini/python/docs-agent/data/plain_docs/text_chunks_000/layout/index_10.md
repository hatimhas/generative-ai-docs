When a layout is too large to fit a device, a yellow
and black striped pattern appears along the affected edge.
Here is an example of a row that is too wide:

Widgets can be sized to fit within a row or column by using the
Expanded widget. To fix the previous example where the
row of images is too wide for its render box,
wrap each image with an Expanded widget.


code-excerpt "layout/sizing/lib/main.dart (expanded-images)" replace="/Expanded/[!$&!]/g"?
  ```dart
  Row(
    crossAxisAlignment: CrossAxisAlignment.center,
    children: [
      [!Expanded!](
        child: Image.asset('images/pic1.jpg'),
      ),
      [!Expanded!](
        child: Image.asset('images/pic2.jpg'),
      ),
      [!Expanded!](
        child: Image.asset('images/pic3.jpg'),
      ),
    ],
  );
  ```





  **App source:** [sizing](}/layout/sizing)


Perhaps you want a widget to occupy twice as much space as its
siblings. For this, use the Expanded widget flex property,
an integer that determines the flex factor for a widget.
The default flex factor is 1. The following code sets
the flex factor of the middle image to 2:


code-excerpt "layout/sizing/lib/main.dart (expanded-images-with-flex)" replace="/flex.*/[!$&!]/g"?
  ```dart
  Row(
    crossAxisAlignment: CrossAxisAlignment.center,
    children: [
      Expanded(
        child: Image.asset('images/pic1.jpg'),
      ),
      Expanded(
        [!flex: 2,!]
        child: Image.asset('images/pic2.jpg'),
      ),
      Expanded(
        child: Image.asset('images/pic3.jpg'),
      ),
    ],
  );
  ```





  **App source:** [sizing](}/layout/sizing)
