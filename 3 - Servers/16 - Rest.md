# Rest (Representation State Transfer)

Rest is an API paradigm that is built on top of HTTP protocol, which benefit clients to communicate with the server using all HTTP methods while exchanding messages over the network.
This architectural style requires that client and server are develop separetely, while the only point of connection if the paradigm used to communicate client/server.

It is important to state that Rest is a stateless paradigm, which mean that servers doesn't track previous client calls.
Which makes sense, imagine a system admin trying to horizontal scale his server, how the client will know which server it previous called?

When a client call for a server, the server process its request and return the desired response.
There is no way to say which server of a cluster of the same service the client has called.

Example:

A client want to list the records of students using the follow resource:

    GET http://myschool.com/students?offset=0&limit=10

The server will return the list of students, using the criteria of 10 records in the page 0. And that is it. Client can eventually perform a new request, that may or may not be processed by the same server, asking 10 more records in page 1. And so on.
A client may hold data that allows to track which "state" the data is at that moment, but server doe not track any of it.

## Data exchange

In modern systems the data type used to exchange through request messages are called json. There are other types of data, such as XML, or binary.
Json is a text data type that is similar to a python dictionary or a hashmap. With unique key/value pairs.
Each key is a string that may hold any type of value, int, double, strings, lists, or even other dictionaries.
The follow are an example of a Json that may be used to POST to a Rest API or returned by a Rest API:

    {
        "name": "Mr. Hands",
        "age": 35,
        "profession": "fixer",
        "address": {
            "zone": "Pacifica",
            "district": "Dogtown",
            "address": "Heaviest Hearts Club"
        },
        "npc": True,
        "gis": [
            "dogtown Saints",
            "heaviest of hearst",
            "prototype in the Scraper",
            "Road of redemption",
            "spy in the jungle",
            "talent academy"
        ]
    }

Json can also be a list of objects like the exemplified above:

    [
        {
            "name": "Mr. Handrs",
            "age": 35
        },
        {
            "name": "Solomon Reed",
            "age": 46
        },
        {
            "name": "Judy Alvarez",
            "age": 27
        },
        "offset": 0,
        "limit": 3
    ]

## Limitations

As everything in software architecture and system design, there are trade-offs.
Rest paradigm is no different. Using this approach to develop a server API can be faster and easy, but there come with some limitations.

- Json responses can be too big, which can impact to the response latency.
- Requests can lead to over-fetch, which means, sometimes you want just a few data from a response, but because the way Rest operates it can return too much data that you probably don't want and don't need to use.
- Requests can lead to under-fetch, which is similar to it sibling, but in this case, you request need some pieces of data that our server response doesn't return, which force you to make extra requests to different resources, just to get that extra piece of info.
