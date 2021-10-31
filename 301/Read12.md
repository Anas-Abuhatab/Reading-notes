# CRUD

* CREATE
The create action is usually implemented via HTTPs POST method. In RESTful APIs, these endpoints are used to create new resources or access tokens.

Status Codes

200 OK - It’s the basic status code to tell the client everything went good. Since we don’t create endpoint accessible resource when creating an access token, we can use 200 as a status for that action.
201 Created - The most fitting for Create operations. This code should signal backend-side resource creation and come along with a Location header that defines the most specific URL for that newly created resource. It’s also a good idea to include appropriate representation of the resource or at least one or more URLs to that resource in the response body.
202 Accepted - Often used for asynchronous processing. This code tells the client that the request was valid, but its processing will finish sometime in the future. The response body should include an URL to the finished resource with some information about when it will be available, or an URL to some monitoring endpoint that tells the client when the resource is available.
303 See Other - Like the 202 code but using a Location header field in response to informing the client about the location of the created resource or an endpoint that lets the client check for the status of the creation process. Some clients follow the status codes of the Redirect-class automatically. This code is usually only used for POST requests.

* No Permissions
Often clients can’t access every resource on the backend, so we need a way to tell them about it.

Status Codes

401 Unauthorized - The client hasn’t authorized itself to the backend yet and the server may give it access after that has happened.
403 Forbidden - The client has authorized or doesn’t need to authorize itself, but still has no permissions to access the resource.
404 Not Found - If 401 or 403 is the case, but the backend doesn’t want to tell the client that the resource exists for security reasons.

* The HTTP creators thought about many status codes when designing it and even added a bunch of new ones over the years. If they’re used correctly they can help to improve developer experience greatly by leveraging automatic redirect follows of clients and explaining what happened more clearly.

Sometimes there are multiple codes we could use for one particular case, the important thing is that we keep our usage consistent over the whole API surface.
