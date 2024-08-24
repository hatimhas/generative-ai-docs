Avoid writing code that checks whether the device you're
running on is a "phone" or a "tablet", or any other type
of device when making layout decisions.
What space your app is actually given to render in
isn't always tied to the full screen size of the device.
Flutter can run on many different platforms,
and your app might be running in a resizeable window on ChromeOS,
side by side with another app on tablets in a multi-window mode,
or even in a picture-in-picture on phones.
Therefore, device type and app window size aren't
really strongly connected.
Instead, use MediaQuery to get the size of the window
your app is currently running in.
This isn't only helpful for UI code.
To learn how abstracting out device
capabilities can help your business logic code,
check out the 2022 Google I/O talk,
Flutter lessons for federated plugin development.
