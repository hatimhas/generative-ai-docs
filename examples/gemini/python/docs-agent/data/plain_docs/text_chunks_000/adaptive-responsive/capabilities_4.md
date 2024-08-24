Sometimes you want your code to do something but the
API doesn't exist, or maybe you depend on a plugin feature
that isn't yet implemented on all of the platforms you support.
This is a limitation of what the device can do. 
Those situations are similar to the policy decisions
described above, but these are referred to as capabilities.
Why separate policy classes from capabilities
when the structure of the classes is similar?
The Flutter team has found with productionized apps that making
a logical distinction between what apps can do and
what they should do helps larger products respond to
changes in what platforms can do or require
in addition to your own preferences after
the initial code is written. 
For example, consider the case where one platform adds
a new permission that requires users to interact with
a system dialog before your code calls a sensitive API.
Your team does the work for platform 1 and creates a
capability named requirePermissionDialogFlow.
Then, if and when platform 2 adds a similar requirement
but only for new API versions,
then the implementation of requirePermissionDialogFlow
can now check the API level and return true for platform 2.
You've leveraged the work you already did.
