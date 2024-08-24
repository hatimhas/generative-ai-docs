Use the font's details page to learn more about its static fonts.

To investigate a variable Google font, go to the Google Fonts
   website. Note that in the upper right corner of each font card,
   it says either variable for a variable font, or
   x styles indicating how many styles a static
   font supports.
Make sure that Show only variable fonts is not checked
   and the search field is empty.
Open the Font properties menu. Check the Number of styles
   checkbox, and move the slider to 10+.
Select a font, such as Roboto to open up its details page.
Roboto has 12 styles, and each style is previewed on its details
   page, along with the name of that variation.
In real time, move the pixel slider to preview the font at
   different pixel sizes.
Select the Type tester tab to see the supported styles for
   the font. In this case, there are 3 supported styles.
Select the Glyph tab. This shows the glyphs that the
   font supports.

Use the following API to programmatically alter a static font
(but remember that this only works if the font was designed
to support the feature):

FontFeature to select glyphs
FontWeight to modify weight
FontStyle to italicize

A FontFeature corresponds to an OpenType feature tag
and can be thought of as a boolean flag to enable or disable
a feature of a given font.
The following example is for CSS, but illustrates the concept:
