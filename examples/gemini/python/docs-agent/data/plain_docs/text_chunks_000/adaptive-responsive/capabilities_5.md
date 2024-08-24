We encourage starting with a Policy class initially
even if it seems like you won't make many policy based decisions.
As the complexity of the class grows or the number of inputs expands,
you might decide to break up the policy class by feature
or some other criteria.  
For policy implementation, you can use compile time,
run time, or Remote Procedure Call (RPC) backed implementations.
Compile-time policy checks are good for platforms
where the preference is unlikely to change and where
accidentally changing the value might have large consequences.
For example, if a platform requires that you not
link to the Play store, or requires that you use
a specific payment provider given the content of your app.
Runtime checks can be good for determining if there
is a touch screen the user can use. Android has a feature
you can check and your web implementation could
check for max touch points. 
RPC-backed policy changes are good for incremental
feature rollout or for decisions that might change later.
