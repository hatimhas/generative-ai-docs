On modern desktop applications, it's common to customize
the title bar of your app window, adding a logo for
stronger branding or contextual controls to help save
vertical space in your main UI.

This isn't supported directly in Flutter, but you can use the
bits_dojo package to disable the native title bars,
and replace them with your own.
This package lets you add whatever widgets you want to the
TitleBar because it uses pure Flutter widgets under the hood.
This makes it easy to adapt the title bar as you navigate
to different sections of the app.
