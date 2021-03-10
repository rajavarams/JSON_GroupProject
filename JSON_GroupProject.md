
## What is a Resource
A resource in REST is a similar Object in Object Oriented Programming or is like an Entity in a Database. Once a resource is identified then its representation is to be decided using 
a standard format so that the server can send the resource in the above said format and client can understand the same format.
A resource is an object with a type, associated data, relationships to other resources, and a set of methods that operate on it. It is similar to an object instance in
an object-oriented programming language, with the important difference that only a few standard methods are defined for the resource (corresponding to the standard HTTP GET, POST, PUT and
DELETE methods), while an object instance typically has many methods.


## Creating Resources
A resource can be created by sending a POST request to a URL that represents a collection of resources. POST is the HTTP method that is designed to send loads of data
to a server from a specified resource. If you perform a `POST` request, the server creates a new entry in the database and tells you whether the creation is successful.
In other words, a `POST` request performs an `CREATE` operation.
POST is not idempotent, so it is fine to create multiple resources if the same request is issued multiple times.

Resources are typically created by sending a POST request to the parent collection resource. This creates a new subordinate resources with a newly generated id.
To create resources in a REST environment, we usually use the HTTP POST method. POST creates a new resource of the specified resource type. A resource can be created by sending a POST
request to the URL that represents the collection of resources.

It’s important to know that a request is made up of four things:
Endpoint
Method
Headers
The data or body

The endpoint (or route) is the url you request for.

## Client request
Clients must also send the following headers:
* Content-Type: to specify the media type of the request body
* Accept: to define supported response formats.
For example, a POST request to /projects might be used to create a new project resource at /projects/123.

POST /projects
Content-Type: application/json
Accept: application/json
{
	"name": "My cool project",
    "description": "This is a coding project.." }

## Server Response
After a resource has been created successfully, the server should respond with HTTP 201 (Created). The response should also have a Location header that contains the URI of 
the newly created resource. When needed, the response body can contain the created resource. In this case, a Content-Type header is also required.

HTTP/1.1 201 Created
Location: /projects/123
Content-Type: application/json

{
    "id" : 123,
    "name": "My cool project",
    "description": "This is coding project.."
}

## Different Type of Responses

* 201 Created
The request has succeeded and a new resource has been created as a result. This is typically the response sent after POST requests, or some PUT requests.

* 202 Accepted
The request has been received but not yet acted upon. It is noncommittal, since there is no way in HTTP to later send an asynchronous response indicating the outcome of the request. It is intended for cases where another process or server handles the request, or for batch processing.

* 203 Non-Authoritative Information
This response code means the returned meta-information is not exactly the same as is available from the origin server, but is collected from a local or a third-party copy. This is mostly used for mirrors or backups of another resource. Except for that specific case, the "200 OK" response is preferred to this status.

* 204 No Content
There is no content to send for this request, but the headers may be useful. The user-agent may update its cached headers for this resource with the new ones.

* 205 Reset Content
Tells the user-agent to reset the document which sent this request.

* 206 Partial Content
This response code is used when the Range header is sent from the client to request only part of a resource.