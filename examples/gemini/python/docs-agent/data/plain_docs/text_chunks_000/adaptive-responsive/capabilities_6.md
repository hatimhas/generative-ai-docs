Use a Capability class to define what the code can do.
You might check against the existence of an API,
OS-enforced restrictions,
and physical hardware requirements (like a camera).
A capability usually involves compile or runtime checks.
Use a Policy class (or classes depending on complexity)
to define what the code should do to comply with
App store guidelines, design preferences,
and assets or copy that need to refer to the host device.
Policies can be a mix of compile, runtime, or RPC checks. 
Test the branching code by mocking capabilities and
policies so the widget tests don't need to change
when capabilities or policies change.
Name the methods in your capabilities and policies classes
based on what they are trying to branch, rather than on device type.
