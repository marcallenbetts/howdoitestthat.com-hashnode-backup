## Export curl from mitmproxy


I've been using [mitmproxy](https://mitmproxy.org/) pretty much non-stop for the
past several months. My current daily workflow consists of a proxy and two reverse
proxies.

From anywhere within mitmproxy, entering `?` will display context-sensitive help. For
the most part, the documentation is great. The one thing I was not able to find
was how to export a request as a curl request, which are useful when trying to share
requests with team mates.

After Googling it for a bit, I finally came across how to do it:

- enter `w` to enter export mode
- enter `export.clip curl @focus` to copy curl request to clipboard

It works, but I'm still going to reference my notes I need to remember the
exact syntax. Luckily, mitmproxy has [key binding](https://docs.mitmproxy.org/stable/tools-mitmproxy/)
support. So, by adding the following to `~/.mitmproxy/keys.yaml`
I now have a shortcut to copy a curl request from mitmproxy.

```
-
  key: c
  cmd: export.clip curl @focus
```
