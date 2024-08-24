Apps using the Router class integrate with the browser History API to provide
a consistent experience when using the browser's back and forward buttons.
Whenever you navigate using the Router, a History API entry is added to the
browser's history stack. Pressing the back button uses [reverse
chronological navigation][], meaning that the user is taken to the previously
visited location that was shown using the Router. This means that if the user
pops a page from the Navigator and then presses the browser back button
the previous page is pushed back onto the stack.
