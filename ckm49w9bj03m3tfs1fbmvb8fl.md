## Postman and lodash


I use [lodash](https://lodash.com/) as my goto JS utility library. One
of the main reasons is that it's included with Postman and I'm too lazy to
use one tool in [Postman](https://www.postman.com/) and a different one elsewhere.

What is not immediatley apparent in Postman is that it actually includes
two versions of lodash. The default is (currently) 3.10.1. If you want to use
a newer version (currently 4.17.15), you can by overriding the default.

```
console.log(_.VERSION)
// 3.10.1

_ = require('lodash')
console.log(_.VERSION)
// 4.17.15
```
