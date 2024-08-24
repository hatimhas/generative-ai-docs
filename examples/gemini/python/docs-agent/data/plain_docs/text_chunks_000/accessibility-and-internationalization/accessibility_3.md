For mobile, screen readers (TalkBack, VoiceOver)
enable visually impaired users to get spoken feedback about
the contents of the screen and interact with the UI by using
gestures on mobile and keyboard shortcuts on desktop.
Turn on VoiceOver or TalkBack on your mobile device and
navigate around your app.
To turn on the screen reader on your device, complete the following steps:



On your device, open Settings.
Select Accessibility and then TalkBack.
Turn 'Use TalkBack' on or off.
Select Ok.

To learn how to find and customize Android's
accessibility features, view the following video.




On your device, open Settings > Accessibility > VoiceOver
Turn the VoiceOver setting on or off

To learn how to find and customize iOS
accessibility features, view the following video.



For web, the following screen readers are currently supported:
Mobile browsers:

iOS - VoiceOver
Android - TalkBack

Desktop browsers:

macOS - VoiceOver
Windows - JAWs & NVDA

Screen readers users on web must toggle the
"Enable accessibility" button to build the semantics tree.
Users can skip this step if you programmatically auto-enable
accessibility for your app using this API:
```dart
import 'package:flutter/material.dart';
import 'package:flutter/semantics.dart';
void main() {
  runApp(const MyApp());
  SemanticsBinding.instance.ensureSemantics();
}
```


Windows comes with a screen reader called Narrator
but some developers recommend using the more popular
NVDA screen reader. To learn about using NVDA to test
Windows apps, check out
Screen Readers 101 For Front-End Developers (Windows).
On a Mac, you can use the desktop version of VoiceOver,
which is included in macOS.

On Linux, a popular screen reader is called Orca.
It comes pre-installed with some distributions
and is available on package repositories such as apt.
To learn about using Orca, check out
Getting started with Orca screen reader on Gnome desktop.



Check out the following video demo to see Victor Tsaran,
using VoiceOver with the now-archived Flutter Gallery web app.
Flutter's standard widgets generate an accessibility tree automatically.
However, if your app needs something different,
it can be customized using the Semantics widget.
When there is text in your app that should be voiced
with a specific voice, inform the screen reader
which voice to use by calling TextSpan.locale.
Note that MaterialApp.locale and Localizations.override
don't affect which voice the screen reader uses.
Usually, the screen reader uses the system voice
except where you explicitly set it with TextSpan.locale.
