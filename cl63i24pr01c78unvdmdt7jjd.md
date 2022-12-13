# Quack scripts

Start with the obvious: quack scripts have nothing to do with [rubber duck debugging](https://en.wikipedia.org/wiki/Rubber_duck_debugging). The only thing they have in common is ducks. I could have chosen pretty much anything for this but I chose ducks. Because ducks are awesome.

So what is it? Basically, it's a script that provides an auditory alert when something happens. Not really different than any other type of monitoring, but it's usual an ad hoc script I create that I need for the task at hand and is usually discarded the same day it's created.

Here's a couple examples I've created recently.

I had a test that was causing backend server to run out of memory. I needed to re-run the tests to try to figure out exactly where in the run the server was giving up. Normally I'd just watch the server logs side by side with the test output, but my ability to focus on more than one thing at a time is notoriously bad. So here's `quack.sh` to send a curl request every ten seconds at quack at me when the server doesn't respond.

```plaintext
while [ 1 -eq 1 ]
do
    RES=`curl -s https://myhost.com/heartbeat`
    TIMESTAMP=`date +"%T"`
    echo $TIMESTAMP $RES
    if [ "$RES" != "I'm Alive!" ]
        then
            afplay quack.wav
        fi
    sleep 10
done
```

More recently, I was testing some functionality that uses websocket connections. Using browser debug or proxy tools will show the websocket requests, but not always in the most intuitive manner. So I decided to combine a [mitmproxy script](https://howdoitestthat.com/mitmproxy-scripts) with a quack script so I'd get alerted when my web client received a websocket message back from the server.

For this one, in addition to quacking, I write the messages to a log file with a timestamp.

```plaintext
import os

from mitmproxy import ctx, http
import datetime


def websocket_message(flow: http.HTTPFlow):
    assert flow.websocket is not None
    if flow.request.host == "myhost.com":

        # get the latest message
        message = flow.websocket.messages[-1]

        # was the message sent from the client or server?
        if message.from_client:
            message = f"Client sent a message: {message.content!r}\n"
        else:
            message = f"Server sent a message: {message.content!r}\n"

        ctx.log.info(message)
        os.system("afplay quack.wav")
        time = datetime.datetime.now()
        file = open("quack.log", "a")
        file.write("%s - %s" % (time.strftime("%X"), message))
        file.close()
```