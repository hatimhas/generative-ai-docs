Desktop and mobile users expect scrollbars,
but they expect them to behave differently on different platforms.
Mobile users expect smaller scrollbars that only appear
while scrolling, whereas desktop users generally expect
omnipresent, larger scrollbars that they can click or drag.
Flutter comes with a built-in Scrollbar widget that already
has support for adaptive colors and sizes according to the
current platform. The one tweak you might want to make is to
toggle alwaysShown when on a desktop platform:
code-excerpt "lib/pages/adaptive_grid_page.dart (scrollbar-always-shown)"?
dart
return Scrollbar(
  thumbVisibility: DeviceType.isDesktop,
  controller: _scrollController,
  child: GridView.count(
    controller: _scrollController,
    padding: const EdgeInsets.all(Insets.extraLarge),
    childAspectRatio: 1,
    crossAxisCount: colCount,
    children: listChildren,
  ),
);
This subtle attention to detail can make your app feel more
comfortable on a given platform.
