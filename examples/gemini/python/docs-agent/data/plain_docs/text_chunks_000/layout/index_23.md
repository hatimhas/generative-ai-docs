Uses `ListView` to display a list of businesses using
  `ListTile`s. A `Divider` separates the theaters from
  the restaurants.

  **App source:** [grid_and_list](}/layout/grid_and_list)




  Uses `ListView` to display the `Colors` from
  the Material 2 Design palette
  for a particular color family.

  **Dart code:**
  [`colors_demo.dart`](}/layout/gallery/lib/colors_demo.dart)


code-excerpt "layout/grid_and_list/lib/main.dart (list)" replace="/\ListView/[!$&!]/g;"?
```dart
Widget _buildList() {
  return !ListView!}
ListTile _tile(String title, String subtitle, IconData icon) {
  return ListTile(
    title: Text(title,
        style: const TextStyle(
          fontWeight: FontWeight.w500,
          fontSize: 20,
        )),
    subtitle: Text(subtitle),
    leading: Icon(
      icon,
      color: Colors.blue[500],
    ),
  );
}
```
