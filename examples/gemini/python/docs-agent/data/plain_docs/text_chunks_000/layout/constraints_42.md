Knowing the general layout rule is necessary, but it's not enough.
Each widget has a lot of freedom when applying the general rule,
so there is no way of knowing how it behaves by just reading
the widget's name.
If you try to guess, you'll probably guess wrong.
You can't know exactly how a widget behaves unless
you've read its documentation, or studied its source-code.
The layout source-code is usually complex,
so it's probably better to just read the documentation.
However, if you decide to study the layout source-code,
you can easily find it by using the navigating capabilities
of your IDE.
Here's an example:


Find a Column in your code and navigate to its
  source code. To do this, use command+B (macOS)
  or control+B (Windows/Linux) in Android Studio or IntelliJ.
  You'll be taken to the basic.dart file.
  Since Column extends Flex, navigate to the Flex
  source code (also in basic.dart).


Scroll down until you find a method called
  createRenderObject(). As you can see,
  this method returns a RenderFlex.
  This is the render-object for the Column.
  Now navigate to the source-code of RenderFlex,
  which takes you to the flex.dart file.


Scroll down until you find a method called
  performLayout(). This is the method that does
  the layout for the Column.




Original article by Marcelo Glasberg
Marcelo originally published this content as
Flutter: The Advanced Layout Rule Even Beginners Must Know
on Medium. We loved it and asked that he allow us to publish
in on docs.flutter.dev, to which he graciously agreed. Thanks, Marcelo!
You can find Marcelo on GitHub and pub.dev.
Also, thanks to Simon Lightfoot for creating the
header image at the top of the article.
:::note
To better understand how Flutter implements layout
constraints, check out the following 5-minute video:

:::
