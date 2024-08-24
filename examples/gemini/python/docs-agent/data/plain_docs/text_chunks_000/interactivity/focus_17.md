The FocusTraversalPolicy is the object that determines which widget is next,
given a request and the current focus node. The requests (member functions) are
things like findFirstFocus, findLastFocus, next, previous, and
inDirection.
FocusTraversalPolicy is the abstract base class for concrete policies, like
ReadingOrderTraversalPolicy,  OrderedTraversalPolicy and the
DirectionalFocusTraversalPolicyMixin classes.
In order to use a FocusTraversalPolicy, you give one to a
FocusTraversalGroup, which determines the widget subtree in which the policy
will be effective. The member functions of the class are rarely called directly:
they are meant to be used by the focus system.
