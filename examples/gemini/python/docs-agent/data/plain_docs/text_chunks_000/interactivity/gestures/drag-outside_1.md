If you want to implement drag and drop within
your application and also between your
application and another (possibly non-Flutter) app,
check out the super_drag_and_drop package.
To avoid implementing two styles of drag and drop,
one for drags outside of the app and another for
dragging inside the app,
you can supply local data to the package to
perform drags within your app.
Another difference between this approach and
using Draggable directly,
is that you must tell the package up front
what data your app accepts because the platform
APIs need a synchronous response, which doesn't
allow an asynchronous response from the framework.
An advantage of using this approach is that it
works across desktop, mobile, and web.
