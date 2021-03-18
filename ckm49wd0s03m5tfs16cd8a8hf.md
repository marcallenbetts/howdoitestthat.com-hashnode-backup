## Setting browser debugger for inspecting elements


I find myself lately in the unfortunate position of doing a lot of web-based UI
automation. Which means I spend a lot of time in the inspector tab of my browser's
developer tools. I only recently learned you can send a debug command to stop the
DOM from changing while you're trying to inspect it. I wish I had just asked
about this years ago.

```
setTimeout(function(){debugger;}, 5000)
```

1. Open debug console in browser
2. Enter the script above
3. Execute script
4. Get browser to the state you want to inspect when debugger starts in 5 seconds