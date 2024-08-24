Apps should retain or restore app state
as the device rotates, changes window size,
or folds and unfolds. 
By default, an app should maintain state.
If your app loses state during device configuration,
verify that the plugins and native extensions
that your app uses support the
device type, such as a large screen.
Some native extensions might lose state when the
device changes position.
For more information on a real-world case
where this occurred, check out 
Problem: Folding/unfolding causes state loss
in Developing Flutter apps for Large screens,
a free article on Medium.
