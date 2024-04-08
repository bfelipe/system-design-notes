# HTTP (Hypertext Transfer Protocol)

We have briefly mentioned HTTP, but we haven't got into details what it is and how it works.
HTTP is an application protocol that allows client and server communicate over TPC in a specified matter. In other words, HTTP is an specification which the client and server agree to structure the data which is gonna be transfered between them. So both can encode and decode for read and write its content.

See more about [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP)

## HTTP structure

HTTP obey a specification that structure the way our data must to be in order to be transfered from client to server, and from server to client.
We gonna take a quick look on this anatomy.

## Client/Server model

In web systems context we may hear the concept of client/server model. What is this exactly?
A client is an agent that trigger the call to a server, it may be a device such as phone, an web page, or even another server that needs data from another server or just trigger an event to be processed.
A server by other hands is the agent that holds the data, or provide the functionality that the client expect to use or holds the procedures to process an event.

## HTTP Message - client

When we transfer data in a client/server model we name it HTTP message.
An HTTP Message from client is often called a request, it have the follow structure:

- Start Line
- Headers
- Blank Line
- Body (optional)

## Start Line

A Start Line from a HTTP Message is like the header of a letter. It holds the follow information for the request:

- Request Method
- Request Path
- Protocol Version

A raw Start Line may look like this:

    GET /docs HTTP/1.1

## Request Method

HTTP works with different methods for different contexts.
- GET methods are often used when the context of the request is to fetch data from a given path.
- POST methods are used in the context of sending data to a given path, servers that expect data to be simple processed or saved in a database often use this method.
- PUT methods are used in similar context as POST, it often send data alonside its request to be saved or even updated in an already existing data record.
- DELETE methods are used in the context when you expect to remove certain data or entire record specified by the request path.

There are other HTTP methods such as CONNECT, HEAD, PATCH, TRACE, OPTIONS. You can take a look on them at the documentation of the IETF (Internet Engineering Task Force). This guys are the ones who back the old days not just created the internet but also defined specifications to how communication across the internet should be done.

See more about [HTTP Methods](https://www.rfc-editor.org/rfc/rfc2616#section-9)

We already know what a Path looks like from a previous section when we spoke about URLs.
Protocol Version there is no much about to talk about it, since it just says which version of the protocol is being used.
Nowadays we have HTTP/1.1 and HTTP/1.2. This second version expand the capabilities of the first version with extra features, such as data streaming, but it goes beyond this study notes. I higly recommend you to check on HTTP 2 by your own.

## Headers

Headers are often used as a list of key/value pairs of metadata. It holds informations about the request, and even can be used to send extra data that can be used during the request processing such as authorization token and so on.

A raw headers can look like this:

    Host: domain.com
    User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:124.0) Firefox/124.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate, br
    DNT: 1
    Sec-GPC: 1
    Connection: keep-alive
    Upgrade-Insecure-Requests: 1
    Sec-Fetch-Dest: document
    Sec-Fetch-Mode: navigate
    Sec-Fetch-Site: cross-site
    TE: trailers

## Body

Sometimes an HTTP Messages may not contain a Body data, so it simply end with and empty Blank Line.
But in most cases, HTTP Messages contain data sent by the client. It may have my forms and sizes, such as images, videos, text, or uncommon types such as XML.
Nowadays we common transfer data in a format called json.
It may look something like this:

    {
        "name": "Alice",
        "age": 32,
        "address": {
            "street": "abc",
            "number": 123
        },
        "contact": [
            {
                "type": "phone",
                "number": "000-000-000",
            },
            {
                "type": "email",
                "address": "email@email.com"
            }
        ],
        "active_user": true
    }

## HTTP Message - server

Servers also return HTTP Messages, is is called response. As requests, responses also have a structure declared by the HTTP specification.

- Start Line
- Headers
- Blank Line
- Body

## Start Line

Different from the request Start Line, a response Start Line looks much more simple.

- Protocol Version
- Status Code
- Status Message

A raw Start line from a response may look like this:

    HTTP/1.1 200 OK

## Status Code and Status Message

Each response comes along with a Status Code (integer) and a Status Message which is linked to the Status Code.
The are several Status Code available for each use case for scenarios where the server successfully process its request, not find a given path or even couldn't process properly the request due an internal error.
You can check all status code available with their meaning here [HTTP Status Code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

## TLS (Transport Layer Security)

HTTP as an application protocol can easily transfer data from client to server and vice and versa. But this brings us an issue. It is easily accessible over the network, so anyone can look what the HTTP Messages are transfering and in the worst scenario, can easily altere its content.
This is where TLS comes in.

TLS allow our requests to be unnacessible by man-in-the-middle attackers by encrypting its content, and allows us also to ensure the content is unnaltered during the transmission over the network.

**Fun fact. Before TLS, we used to call it SSL.**

So now, everytime we see a link using HTTPS it means it is using HTTP protocol with TLS to secure its transmission.