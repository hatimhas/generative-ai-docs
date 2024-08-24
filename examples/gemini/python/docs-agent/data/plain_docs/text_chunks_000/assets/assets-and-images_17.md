In your Flutter project's root directory, navigate to
.../android/app/src/main/res. The various bitmap resource
folders such as mipmap-hdpi already contain placeholder
images named ic_launcher.png. Replace them with your
desired assets respecting the recommended icon size per
screen density as indicated by the Android Developer Guide.

:::note
If you rename the .png files, you must also update the
corresponding name in your AndroidManifest.xml's
<application> tag's android:icon attribute.
:::
