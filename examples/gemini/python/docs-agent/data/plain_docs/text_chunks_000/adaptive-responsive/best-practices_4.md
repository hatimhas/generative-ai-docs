Avoid using MediaQuery's orientation field
or OrientationBuilder to switch between
different app layouts. This is similar to the
guidance of not checking device types to determine
screen size. The device's orientation also doesn't
necessarily inform you of how much space your app window has.
Instead, use MediaQuery's sizeOf or LayoutBuilder,
as discussed in the General approach page.
Then use adaptive breakpoints like the ones that
Material recommends.
