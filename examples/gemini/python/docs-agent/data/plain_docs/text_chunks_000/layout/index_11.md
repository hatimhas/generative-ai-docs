By default, a row or column occupies as much space along its main axis
as possible, but if you want to pack the children closely together,
set its mainAxisSize to MainAxisSize.min. The following example
uses this property to pack the star icons together.


code-excerpt "layout/pavlova/lib/main.dart (stars)" replace="/mainAxisSize.*/[!$&!]/g; /\w+ \w+ = //g; /;//g"?
  ```dart
  Row(
    [!mainAxisSize: MainAxisSize.min,!]
    children: [
      Icon(Icons.star, color: Colors.green[500]),
      Icon(Icons.star, color: Colors.green[500]),
      Icon(Icons.star, color: Colors.green[500]),
      const Icon(Icons.star, color: Colors.black),
      const Icon(Icons.star, color: Colors.black),
    ],
  )
  ```





  **App source:** [pavlova](}/layout/pavlova)
