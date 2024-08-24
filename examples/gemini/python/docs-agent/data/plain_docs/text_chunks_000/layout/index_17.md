This layout consists of a column with two rows, each containing
2 images. A Container is used to change the background color
of the column to a lighter grey.


code-excerpt "layout/container/lib/main.dart (column)" replace="/\bContainer/[!$&!]/g;"?
  ```dart
  Widget _buildImageColumn() {
    return [!Container!](
      decoration: const BoxDecoration(
        color: Colors.black26,
      ),
      child: Column(
        children: [
          _buildImageRow(1),
          _buildImageRow(3),
        ],
      ),
    );
  }
  ```






A Container is also used to add a rounded border and margins
to each image:
code-excerpt "layout/container/lib/main.dart (row)" replace="/\bContainer/[!$&!]/g;"?
```dart
Widget _buildDecoratedImage(int imageIndex) => Expanded(
      child: !Container!,
      ),
    );
Widget _buildImageRow(int imageIndex) => Row(
      children: [
        _buildDecoratedImage(imageIndex),
        _buildDecoratedImage(imageIndex + 1),
      ],
    );
```
You can find more Container examples in the tutorial.
App source: container
