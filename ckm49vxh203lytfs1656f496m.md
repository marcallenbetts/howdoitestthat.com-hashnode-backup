## Proxy command line processes


Anybody who has worked with me for more than five minutes know that I have two
basic categories of test tools that I gravitate toward: proxies and command line
tools.

Proxies are great because they give you valuable insight in to the network requests
your application is making that aren't usually visible from within the app. Command line
tools are great for lots of reasons, mainly because junior developers and less tech savvy
people on the team will think you are some sort of super hacker wizard if they walk by and see
you frantically typing in a terminal window.

But it's not alwasy obvious how to get your terminal to send network traffic to a proxy.

These days I use [Postman](https://www.getpostman.com/) as my API test tool of choice. It's
a solid tool for testing and includes a commmand line runner (Newman). When using the GUI,
it's really easy to see the requests and responses. When running Newman from the command line, not
so much.

So how do you configure CLIs to use a local proxy? Turns out you just need to set the `http_proxy`
environment variable. And when you're done you can `unset` it. (Examples below use the default port for [Charles Proxy](https://www.charlesproxy.com/)).

### TL;DR

- `export http_proxy=http://localhost:8888`
- `export https_proxy=http://localhost:8888`
- `unset http_proxy`
- `unset https_proxy`
