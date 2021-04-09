## Postman and faker


I use Postman for a lot of my API testing, including generating test
data. For a long time I wished Postman would add faker to it's limited
list of included JS libraries. Then I realized it was already there, but
the documentation around it is just severely lacking.

The Postman docs has a [variable list](https://learning.postman.com/docs/postman/variables-and-environments/variables-list/),
but doesn't do a good job of explaining where they can be used. They work in the body
or URL of a request, but not in a pre-request script or in a test.

To work around that, do something like this in a test or pre-request script:

`pm.variables.replaceIn("{{$randomProductName}}")`
