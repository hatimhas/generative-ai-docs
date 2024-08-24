Most real-world apps have the need to adapt to the
capabilities and policies of different devices and platforms.
This page contains advice for how to
handle these scenarios in your code.
Consider the unique strengths and weaknesses of different devices.
Beyond their screen size and inputs, such as touch, mouse, keyboard,
what other unique capabilities can you leverage?
Flutter enables your code to run on different devices,
but strong design is more than just running code.
Think about what each platform does best and
see if there are unique capabilities to leverage.
For example: Apple's App Store and Google's Play Store
have different rules that apps need to abide by.
Different host operating systems have differing
capabilities across time as well as each other. 
Another example is leveraging the web's extremely
low barrier for sharing. If you're deploying a web app,
decide what deep links to support,
and design the navigation routes with those in mind.
Flutter's recommended pattern for handling different
behavior based on these unique capabilities is to create
a set of Capability and Policy classes for your app.
