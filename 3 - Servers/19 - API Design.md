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

# Resource naming

Resources naming of our endpoints are usually grouped by domain or business names. Followed by docummenting of what each endpoint does as suggested by Open API.
A good practice is to name resource after a API version using word in singular and avoid using verbs as much as you can, unless you have no better option.
The example I gave previously I broke this rule giving our POST endpoint a name using an action/verb name /collecting, while the recommendation is to not use it, a better alternative for the example I have gave would group this endpoint in /area resource and add into its documentation that POST /area is dedicated for sendind area scanning data. Although this name is not very intuitive if the user is not following alonsig the documentation.
So /collecting or /scanning seems more intuitive for this specific case.

# Subresource, Path Param, Query Param, & Pagination

Subresource often occurs when a specific domain provide features that is related to a specific domain, providing beyond features for that group of data.
There is no proper convention for how deep a Subresource should be, but the shortet the best.
A good recommendation is to use Subresources to manage data or group of data that is part of a complex payload, as a hierarchichal interface of access.
For example, in our /collecting resource we have a Payload designed like this.

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

Instead of 'data', lets rename this attribute to 'celestial_body'

    Payload:
        {
            "lat": int,
            "long": int,
            "celestial_code": str
            "celestial_body": {
                "composition: str,
                "atmosphere": str,
                "geology": "str",
                "element_detection": int
            }
        }

Now for our resource, if we desire to access some data in that subgroup of data, or perform some updates we can design our Subresource as follows:

    GET /collecting/{celestial_code}/celestial_body

This will allow us to access only 'celestial_body' data, searching its data using something we haven't talked before. Path Param.
Path Param is a dynamic parameter that is configured in our resource as a mechanism of data fetching.
Lets think how could we update our celestial_body considering this Resource design.

    PUT /collecting/{celestial_code}/celestial_body
    Payload:
        {
            "composition: str,
            "atmosphere": str,
            "geology": "str",
            "element_detection": int
        }
    Response:
        Status Code: 200
        {
            "message": "Data is updated successfully"
        }
        Status code 404
        {
            "message": "celestial_code is not found"
        }
        Status code 400
        {
            "message": "Attribute xyz is wrong format"
        }

Let talk using another example. Now for our /area Resource.
It does provide a resource to fetch data for a specific area using a area_id as Path Param.
Let say we want to see all area already scanned. For this purpose, let say the Resource for it is simple /area

    GET /area
    Response:
        Status Code: 200
        [
            {
                "celestial_code": 'abc'
                "area_id": 123
                "status": 'normal'
            },
            {
                "celestial_code": 'abc'
                "area_id": 456
                "status": 'normal'
            },
            {
                "celestial_code": 'ghi'
                "area_id": 789
                "status": 'anomaly'
            },
        ]

This resource returns a list of O(n) size.
Another thing we haven't spoke is Query Params and Pagination.
Query Params allows you to add filtering features for your resource.
While Pagination works similar to Query Params, but they are designed to limit the amount of data returned by the server and which page our client is accessing at the moment.
Using Pagination in listing data is a must, since we help the server handle a well considerable amount of data, without consuming too much computer resource as memory, and minimizing the response latency, since its not too much data to be transfered over the network. Pagination works with two attributes, offset(the number refered to the page, it start by page 0), and limit(which refer to the number of records returned by the server).
Let see how this work, and change our Response payload structure for better readability too.
Let say we want to filter areas only with celestial_code 'abc'.

    GET /area?celestial_code=abc&offset=0&limit=10
    Response:
        Status Code: 200
        {
            "offset": 0,
            "limit": 10,
            "data": [
                {
                    "celestial_code": 'abc'
                    "area_id": 123
                    "status": 'normal'
                },
                {
                    "celestial_code": 'abc'
                    "area_id": 456
                    "status": 'normal'
                }
            ]
        }

In this case our filter only returned two records of a limit of 10.
It means there is not enough data to populate a list of 10, and that is ok.
If we try to go to offset=1 we probably gonna get a response with an empty list.
We could to another filtering, this time lookinf for areas that present anomalies in celestial_code abc.

    GET /area?celestial_code=abc&status=anomaly&offset=0&limit=10
    Response:
        Status Code: 200
        {
            "offset": 0,
            "limit": 10,
            "data": []
        }

In this example, we have no data that match this criteria, so an empty list is returned.
As you can see, there is much to consider when designing effective APIs.
Things we haven't spoke here is also about how we decoupling resources into its own servers. But this is subject for thins related to microservice design. Which is not the purpose here. Although I hope this content serve as a good start point.