Although the localizations are handled by Flutter,
you need to add the supported languages in the Xcode project.
This ensures your entry in the App Store correctly displays
the supported languages.
To configure the locales supported by your app,
use the following instructions:


Open your project's ios/Runner.xcodeproj Xcode file.


In the Project Navigator, select the Runner project
   file under Projects.


Select the Info tab in the project editor.


In the Localizations section, click the Add button
   (+) to add the supported lanaguages and regions to your
   project. When asked to choose files and reference language,
   simply select Finish.


Xcode automatically creates empty .strings files and
   updates the ios/Runner.xcodeproj/project.pbxproj file.
   These files are used by the App Store to determine which
   languages and regions your app supports.
