## Basic redis-cli usage

Testing caching is hard.

Testing caching is hard because it's a feature that's designed to be invisible to the user. The user doesn't care if the data they get is the result of an API request, served from cache, served from a CDN, etc. Users want to see their data as quickly as possible.

When testing, I don't often want to know all of the details of what's in cache, I just want to know if my request came from cache or not. Enter  [redis-cli](https://redis.io/topics/rediscli).


Start the CLI:
```
$ redis-cli
``` 

Authenticate if you need to:
```
$ auth <password>
```

Monitor cache requests:
```
$ monitor
```

Clear the cache:
```
$ flushall
```

This is just scratching the surface of redis-cli, but a good start to demystifying testing when caching is involved.