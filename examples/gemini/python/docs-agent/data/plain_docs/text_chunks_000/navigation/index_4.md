The Router and Navigator are designed to work together. You can navigate
using the Router API through a declarative routing package, such as
go_router, or by calling imperative methods such as push() and pop() on
the Navigator.
When you navigate using the Router or a declarative routing package, each
route on the Navigator is page-backed, meaning it was created from a
Page using the pages
argument on the Navigator constructor. Conversely, any Route
created by calling Navigator.push or showDialog will add a pageless
route to the Navigator. If you are using a routing package, Routes that are
page-backed are always deep-linkable, whereas pageless routes
are not.
When a page-backed Route is removed from the Navigator, all of the
pageless routes after it are also removed. For example, if a deep link
navigates by removing a page-backed route from the Navigator, all pageless
routes after (up until the next page-backed route) are removed too.
:::note
You can't prevent navigation from page-backed screens using WillPopScope.
Instead, you should consult your routing package's API documentation.
:::
