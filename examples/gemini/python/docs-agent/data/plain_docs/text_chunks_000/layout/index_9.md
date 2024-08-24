You control how a row or column aligns its children using the
mainAxisAlignment and crossAxisAlignment properties.
For a row, the main axis runs horizontally and the cross axis runs
vertically. For a column, the main axis runs vertically and the cross
axis runs horizontally.




The MainAxisAlignment and CrossAxisAlignment
enums offer a variety of constants for controlling alignment.
:::note
When you add images to your project,
you need to update the pubspec.yaml file to access
them—this example uses Image.asset to display
the images.  For more information, see this example's
pubspec.yaml file or Adding assets and images.
You don't need to do this if you're referencing online
images using Image.network.
:::
In the following example, each of the 3 images is 100 pixels wide.
The render box (in this case, the entire screen)
is more than 300 pixels wide, so setting the main axis
alignment to spaceEvenly divides the free horizontal
space evenly between, before, and after each image.


code-excerpt "layout/row_column/lib/main.dart (row)" replace="/Row/[!$&!]/g"?
  ```dart
  [!Row!](
    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
    children: [
      Image.asset('images/pic1.jpg'),
      Image.asset('images/pic2.jpg'),
      Image.asset('images/pic3.jpg'),
    ],
  );
  ```





  **App source:** [row_column](}/layout/row_column)


Columns work the same way as rows. The following example shows a column
of 3 images, each is 100 pixels high. The height of the render box
(in this case, the entire screen) is more than 300 pixels, so
setting the main axis alignment to spaceEvenly divides the free vertical
space evenly between, above, and below each image.


code-excerpt "layout/row_column/lib/main.dart (column)" replace="/Column/[!$&!]/g"?
  ```dart
  [!Column!](
    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
    children: [
      Image.asset('images/pic1.jpg'),
      Image.asset('images/pic2.jpg'),
      Image.asset('images/pic3.jpg'),
    ],
  );
  ```

  **App source:** [row_column](}/layout/row_column)
