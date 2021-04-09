## Android notifications


I've mentioned before that I hate testing mobile apps. One of the things I hate the
most is testing push notifications.

But it turns out that Android does have one feature that makes this less hateful, if you
know where to look. Here's where to look:

- Long press on home screen
- Select `Widgets` option
- Long press `Settings` and place a Setting shortcut on home screen
- Select `Notifications Log`

Now you've got a Notifications Log shortcut icon on your home screen showing you
all the good stuff about your notifications that you previously had to pore through
ADB logs to find, like the complete message and the intent.
