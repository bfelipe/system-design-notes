# WebSocket

## Pooling

When a client perform a request to a server, and our server does have a response with the content we expect, we may try redo a request until we manage to see the data.
Imagine you send a piece of data that is about to be processed and you expect to see a status as response which says that piece of data was completely processed.
But instead you keep seeying the status 'processing'.
In a common HTTP client/server communication we can configure our client to perform consecutive requests until we manage to get that response we want. This technique is called pooling.
But there is a tradeoff. How many request we must to perform until we manage to fetch that desired that? How often we perform that requests?
In any case, waiting too long for the next request can lead to an outdated response for a critical system. An too often requests can overload our servers with unecessary requests.
That is where WebSocket application protocol comes in.

## Bidirectional communication

WebSocket is an application protocol, which allow client and server exchange messages in a bi-directional way through a single connection, different than a common HTTP which after a request is return by the server, the connection is no longer alive.

The client initiate the request with a HTTP request, using a special header saying it has a WebSocket support.
Once the server process the request, it returns a response with status 101 opening a WebSocket connection so both sides can start exchange messages if the server support this type of connection.

Of course, the process is much more complex that, but as a concept it can helps you understand what this protocol initiate before start to be used.
The most common cases which this protocol is used is in cases where real time transmission of data is required. Such as chats, of even bi-directional events (such a delivery guy getting close with your food).
You can try implement your own webSocket apps by your own, many modern web libraries already come with the necessary interfaces to do that.
You can also learn more about WebSocket details here
[WebSocket API ](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
and here 
[WebSocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_servers)

![](/images/7.png)