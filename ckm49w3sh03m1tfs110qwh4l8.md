## Using NGINX as a filtering proxy


The first question I ask when trying to figure out how to test something is "what are the moving parts?" I'm always trying to see what is changing the helps understand what the application is doing. I'm looking for things like database records that are touched or log file output. And in a lot of applications, it's
network requests.

For network requests, knowing how to use a proxy is an invaluable tool. My current proxy of choice is [Charles Proxy](https://www.charlesproxy.com/), but will turn to [mitmproxy](https://mitmproxy.org/) in a pinch.

One of the apps I'm currently testing includes [preflight requests](https://developer.mozilla.org/en-US/docs/Glossary/Preflight_request) for all API requests. I was trying to use Charles to rewrite some of the requests for some of the tests, but couldn't find any way within Charles to distinguish between OPTIONS requests and POST requests. This was causing the OPTIONS requests to get rewritten in a way that the app didn't care for.

The solution I came up with was to use (NGINX)[https://www.nginx.com/] as a proxy to filter the requests before they get to Charles. This allows me to route the OPTIONS request directly to the server to deal with and the POST requests are sent to the proxy where they can manipulated for testing.

The nginx.conf for this setup looks like this:

```
server {
	listen 8085;
	error_page 405 =200 $uri;
	location / {
		if ($request_method = OPTIONS) {
			proxy_pass REMOTE_HOST;
		}
		if ($request_method != OPTIONS) {
			proxy_pass LOCAL_HOST:8084;
		}
	}
}
```

This will run NGINX on port 8085 and redirect all non-OPTIONS requests to a proxy server running on port 8084. The proxy server needs to be configured as a reverse proxy on port 8084.

### TL;DR

1. Configure a reverse proxy to listen on port 8084
2. Configure app to use proxy on port 8085
3. `git clone git@github.com:marcallenbetts/nginx-proxy-and-errors.git`
4. `docker-compose up --build`
