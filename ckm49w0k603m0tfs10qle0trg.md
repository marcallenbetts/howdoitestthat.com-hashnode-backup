## iOS Simulator Proxy


I Google as hard as I could but never could find a way to set a network
proxy for an iOS Simulator. This is where I landed. If there's an easier
way I'd love to hear about it.

```
let configuration = URLSessionConfiguration.default

    configuration.connectionProxyDictionary = [
        "HTTPSEnable": 1,
        "HTTPSProxy": "localhost",
        "HTTPSPort": 8888
    ]
```
