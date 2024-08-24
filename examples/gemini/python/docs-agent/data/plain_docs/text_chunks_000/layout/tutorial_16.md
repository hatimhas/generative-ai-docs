Add an ImageSection widget as the first child in the children list.
Set the image property to the path of the image you added in
Configure your app to use supplied images.
dart diff
  children: [
+   ImageSection(
+     image: 'images/lake.jpg',
+   ),
    TitleSection(
      name: 'Oeschinen Lake Campground',
      location: 'Kandersteg, Switzerland',
