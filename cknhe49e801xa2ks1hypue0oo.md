## Expose port on local machine

Sometimes I need to access a web page or app from my computer during testing.  Usually it's when I'm testing something quickly and don't want to take the time to deploy to a hosted environment or want to quickly share something with a coworker.

Luckily, there's a few ways to do this. All of this function basically the same. I keep all of them around because some of them are not always 100 percent reliable. And enterprise firewall policies are not always friendly to some of them.


Create a test page and expose it via port 8081
```
echo """
<html>
<head><title>test page</title></head>
<body>hey now</body>
</html>
""" > index.html

python -mSimpleHTTPServer 8081
```

[ngrok](https://ngrok.com/)

```
npm install -g ngrok
ngrok http 8081
ngrok help
```

[localtunnel](https://github.com/localtunnel/localtunnel)

```
npm install -g localtunnel
lt --port 8081
```

[serveo](http://serveo.net/)

```
ssh -o ServerAliveInterval=60 -R 80:localhost:8081 serveo.net
```

[localhost.run](http://localhost.run/)

```
ssh -R 80:localhost:8081 ssh.localhost.run
```