Lays widgets out in a grid
Detects when the column content exceeds the render box
  and automatically provides scrolling
Build your own custom grid, or use one of the provided grids:
GridView.count allows you to specify the number of columns
GridView.extent allows you to specify the maximum pixel
  width of a tile

Use MediaQuery.of(context).orientation to create a grid
  that changes its layout depending on whether the device
  is in landscape or portrait mode.


:::note
When displaying a two-dimensional list where it's important which
row and column a cell occupies (for example,
it's the entry in the "calorie" column for the "avocado" row), use
Table or DataTable.
:::
