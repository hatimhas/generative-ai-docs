In this section, add the image file to complete your layout.
Configure your app to use supplied images
To configure your app to reference images, modify its pubspec.yaml file.


Create an images directory at the top of the project.


Download the lake.jpg image and add it to the new images directory.


:::note
   You can't use wget to save this binary file.
   You can download the image from Unsplash
   under the Unsplash License. The small size comes in at 94.4 kB.
   :::

To include images, add an assets tag to the pubspec.yaml file
   at the root directory of your app.
   When you add assets, it serves as the set of pointers to the images
   available to your code.

yaml title="pubspec.yaml" diff
    flutter:
      uses-material-design: true
   +  assets:
   +    - images/lake.jpg
:::tip
Text in the pubspec.yaml respects whitespace and text case.
Write the changes to the file as given in the previous example.
This change might require you to restart the running program to
display the image.
:::
