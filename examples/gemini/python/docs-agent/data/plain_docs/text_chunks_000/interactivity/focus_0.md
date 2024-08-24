This article explains how to control where keyboard input is directed. If you
are implementing an application that uses a physical keyboard, such as most
desktop and web applications, this page is for you. If your app won't be used
with a physical keyboard, you can skip this.
Flutter comes with a focus system that directs the keyboard input to a
particular part of an application. In order to do this, users "focus" the input
onto that part of an application by tapping or clicking the desired UI element.
Once that happens, text entered with the keyboard flows to that part of the
application until the focus moves to another part of the application.  Focus can
also be moved by pressing a particular keyboard shortcut, which is typically
bound to Tab, so it is sometimes called "tab traversal".
This page explores the APIs used to perform these operations on a Flutter
application, and how the focus system works. We have noticed that there is some
confusion among developers about how to define and use FocusNode objects.
If that describes your experience, skip ahead to the best practices for
creating FocusNode objects.
