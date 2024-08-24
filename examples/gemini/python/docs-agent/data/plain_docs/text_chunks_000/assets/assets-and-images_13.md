On iOS the assets are available through the mainBundle.
The lookup key used in, for instance pathForResource:ofType:,
is obtained from lookupKeyForAsset or lookupKeyForAsset:fromPackage:
on FlutterPluginRegistrar, or lookupKeyForAsset: or
lookupKeyForAsset:fromPackage: on FlutterViewController.
FlutterPluginRegistrar is available when developing
a plugin while FlutterViewController would be the choice
when developing an app including a platform view.
As an example, suppose you have the Flutter setting from above.
To access icons/heart.png from your Objective-C plugin code you
would do the following:
objc
NSString* key = [registrar lookupKeyForAsset:@"icons/heart.png"];
NSString* path = [[NSBundle mainBundle] pathForResource:key ofType:nil];
To access icons/heart.png from your Swift app you
would do the following:
swift
let key = controller.lookupKey(forAsset: "icons/heart.png")
let mainBundle = Bundle.main
let path = mainBundle.path(forResource: key, ofType: nil)
For a more complete example, see the implementation of the
Flutter video_player plugin on pub.dev.
The ios_platform_images plugin on pub.dev wraps
up this logic in a convenient category. You fetch
an image as follows:
Objective-C:
objc
[UIImage flutterImageWithName:@"icons/heart.png"];
Swift:
swift
UIImage.flutterImageNamed("icons/heart.png")
