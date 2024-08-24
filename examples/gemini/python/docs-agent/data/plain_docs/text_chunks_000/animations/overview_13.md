Most Animation subclasses take an explicit "parent"
Animation<double>. They are driven by that parent.
The CurvedAnimation subclass takes an Animation<double> class (the
parent) and a couple of Curve classes (the forward and reverse
curves) as input, and uses the value of the parent as input to the
curves to determine its output. CurvedAnimation is immutable and
stateless.
The ReverseAnimation subclass takes an
Animation<double> class as its parent and reverses
all the values of the animation. It assumes the parent
is using a value nominally in the range 0.0-1.0 and returns
a value in the range 1.0-0.0. The status and direction of the parent
animation are also reversed. ReverseAnimation is immutable and
stateless.
The ProxyAnimation subclass takes an Animation<double> class as
its parent and merely forwards the current state of that parent.
However, the parent is mutable.
The TrainHoppingAnimation subclass takes two parents,
and switches between them when their values cross.
