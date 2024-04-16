## API Design

Imagine you are developing a client that exchange data with a REST API server.
It works, it does have a clean resource structure, and you have a well mapped payload for requests and responses.
But before you notice, something changed, that endpoint you use to perform requests no longer works due to changes of rules that deprecated it.

When things like that happens, and clients are not notified, user experience of your developers may be affected, and this also shows a bad sign of bad design choices while designing your API.

Let's design together an example API for a anomaly detection over an unkown area through a robot.

Our service gonna be definer in the follow domain:

    https://probe.planetary.gov

Now we gonna have some resources or endpoints that allows our robot(client) to perform different interactions with our server, there will be only three endpoints:

    POST /collecting
    Payload:
        {
            "lat": int,
            "long": int,
            "celestial_code": str
            "data": {
                "element_detection": int
            }
        }
    Response:
        Status Code: 201
        {
            "area_id": int
        }
    
    GET /area/{area_id}
    Response:
        Status Code: 200
        {
            "celestial_code": str
            "area_id": int
            "status": str
        }
        Status Code: 404
        {
            "message": "Area Id not found because it was not scanned yet"
        }

    PUT /anomaly_area/{area_id}
    Payload:
        {
            "celestial_code": str
            "area_id"
            "status": str,
            "lat": int,
            "long": int
        }
    Response:
        Status code 200
        {
            "message": "Area Id is now label to be avoided"
        }

This is a simple example, but notice that our resources does not have versions in their prefix, which we can't say if there are differences when a new version release, imagine our POST /collecting release a new version with extra data to be sent to the server:

    POST /collecting
    Payload:
        {
            "lat": int,
            "long": int,
            "celestial_code": str
            "data": {
                "composition: str,
                "atmosphere": str,
                "geology": "str",
                "element_detection": int
            }
        }
    Response:
        Status Code: 201
        {
            "area_id": int
        }
    
There is no way to the client know that api now has different rules than the previous one. This is where versioning your resources come along well. You can use it as a flag for your clients to know that previous versions of that endpoint is now deprecated, and now a new version requires more data to continue the mission of our planetary robot.
Changing our resources from:

    POST /collecting
    
To 

    POST /v1/collecting

Allows client to know it is using a version 1 of that API.
Now, with this new verion which expect new data into its data collection, we could easily define:

    POST /v2/collection

You may decide to keep v1 up and running for robots that opperates in other missions, but for this specific one, a v2 will allow that robot send more data to the server in such way it may have extra insight over that astro location.
Retrocompatibility is something that may happens in some cases, but it is also important to notify your clients about changes that may affect their application behavior, not just about resources calling, but also payload to be sent to the request, or different schemas of responses.

There is a well known specification know as Open API, which define standards, rules and tools to define and document REST APIs.
A tool that is commonly used to help engineers to documents their APIs over Open API specification is Swagger.
Swagger can be used as a standalone documentation tool, written manually or, used as a pluging in your prefered web framework.

You can see more about [Open API](https://www.openapis.org/what-is-openapi)

You can see more about [Swagger](https://swagger.io/docs/specification/2-0/what-is-swagger/)

You can seee more about [Swagger Documentation](https://swagger.io/solutions/api-documentation/)