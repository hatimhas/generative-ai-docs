Both Android and iOS contain system settings to configure the desired font
sizes used by apps. Flutter text widgets respect this OS setting when
determining font sizes.
Font sizes are calculated automatically by Flutter based on the OS setting.
However, as a developer you should make sure your layout has enough room to
render all its contents when the font sizes are increased.
For example, you can test all parts of your app on a small-screen
device configured to use the largest font setting.
