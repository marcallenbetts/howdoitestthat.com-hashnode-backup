## Python SimpleHTTPServer


This one line is the sum total of my knowledge of Python. Unless you count "Python? That's the one that's really picking about spacing, right?"

A few years back I worked on a system that did web scraping for content. So when testing that we were gathering web pages correctly, it was useful to have a web server up and running. Being generally lazy, I opted for the path of least resistance: use web servers that other people maintained for me.

So I had countless free hosting accounts with all the shadiest free hosting outfits a Google search would return. Most of which would disappear without a trace a few months later.

Later, one of the devs introduced me to Python's SimpleHTTPServer. It's pretty much what the name implies. A simple http server that will serve up static content to GET requests. This is also my goto for quickly mocking or modding an API response for a web page or a mobile app.

### TL;DR

`python -mSimpleHTTPServer 8081`

### Update for Python 3
`python3 -mhttp.server 8081`
