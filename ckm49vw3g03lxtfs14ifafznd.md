## Android test utils


I haven't had to do much mobile app testing recently, but last week I got dragged back in
to it for an afternoon. I was very quickly reminded how much I hate testing mobile apps.

The task I needed to accomplish was fairly straightforward: log in with a dozen or so
test accounts and verify that the accounts had been created correctly. This was going
to be a one off activity so trying to automate it would have little ROI.

But just having to type a dozen usernames and passwords on a phone keyboard is enough
to try my patience, so I fall back to using [Android Debug Bridge](https://developer.android.com/studio/command-line/adb).

The problem is that I don't use adb often enough to remember how to use it. So I decided
to write a simplified wrapper for it to make it simple to use the small subset of commands
that I actually need, specifically sending text and taking screenshots.

If situations change and I get sucked back in to the mobile testing world, I may spend
some more time making this more usefull.

### TL;DR

- `git clone git@github.com:marcallenbetts/android-test-util.git`
- `npm install`
- `node atu.js`
- `help`
