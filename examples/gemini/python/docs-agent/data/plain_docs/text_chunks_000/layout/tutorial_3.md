Add the following code after the MyApp class.
code-excerpt "step2/lib/main.dart (title-section)"?
```dart
class TitleSection extends StatelessWidget {
  const TitleSection({
    super.key,
    required this.name,
    required this.location,
  });
final String name;
  final String location;
@override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.all(32),
      child: Row(
        children: [
          Expanded(
            /1/
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                /2/
                Padding(
                  padding: const EdgeInsets.only(bottom: 8),
                  child: Text(
                    name,
                    style: const TextStyle(
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                ),
                Text(
                  location,
                  style: TextStyle(
                    color: Colors.grey[500],
                  ),
                ),
              ],
            ),
          ),
          /3/
          Icon(
            Icons.star,
            color: Colors.red[500],
          ),
          const Text('41'),
        ],
      ),
    );
  }
}
```


To use all remaining free space in the row, use the Expanded widget to
   stretch the Column widget.
   To place the column at the start of the row,
   set the crossAxisAlignment property to CrossAxisAlignment.start.
To add space between the rows of text, put those rows in a Padding widget.
The title row ends with a red star icon and the text 41.
    The entire row falls inside a Padding widget and pads each edge
    by 32 pixels.
