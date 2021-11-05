## mitmproxy scripts

I've been using a mitmproxy for a few years now and have posted about it a few times. One feature that I've only recently begun using is the its script feature. Which is a shame, because this is an incredibly powerful feature. As a bonus, it's been forcing me to learn a little bit more Python.

Here's a couple examples. One for how to use the script to alter a network request and another to handle a response.

Add a 5 to 7 second delay to every request:
```
import random
from time import sleep
from mitmproxy import http


def request(flow: http.HTTPFlow) -> None:
    delay = random.uniform(5, 7)
    sleep(delay)
```


Intercept response and randomly return error for a percentage of the responses:

```
import random
from mitmproxy import http
from mitmproxy import ctx

# percentage of requests to fail
ERROR_RATE = 10
ctx.log.info(f"Setting errorRate to {ERROR_RATE}")

# list of failure codes to use
ERROR_CODES = [400, 403, 500, 502, 503, 504]


def response(flow: http.HTTPFlow) -> None:
    if random.randrange(1, 101) <= ERROR_RATE:
        flow.response.status_code = random.choice(ERROR_CODES)
        flow.response.content = None
``` 

To use these scripts, pass them as a command line argument when starting mitmproxy:
```
mitmproxy --listen-port 8989 --ssl-insecure 
--set console_mouse=false -s myscript.py
```

I use these scripts mostly when testing mobile apps to control requests between app and backend server. Here are some other examples I've explored:
* Add error responses for specific endpoints
* Overriding data in response body (ex. override a config request without having to make backend changes)
* Schema validation of request and response body